# מנגנוני ההרחבה של Claude Code — ממצאים ממנה 1

- מקורות: S-001 עד S-008 (ראו `research/sources.md`)
- תאריך גישה: 2026-11-16
- רישיון: תיעוד Anthropic. נשמרים כאן רק סיכום וציטוטים קצרים, עם קישור למקור.

ממצאים שמשפיעים ישירות על תכנון ה-Harness. כל ממצא מסומן כ**עובדה** (מתועד במקור) או כ**הסקה** (שלי).

---

## 1. הוראות הן בקשה; Hooks הם אכיפה

- **עובדה:** "An instruction like 'never edit `.env`' in CLAUDE.md or a skill is a request, not a guarantee. A `PreToolUse` hook that blocks the edit is enforcement." (S-007)
- **עובדה:** CLAUDE.md ו-auto memory נטענים כ-context, "not enforced configuration" (S-006).
- **עובדה:** Hook שנכשל לא חוסם כברירת מחדל — "a policy hook with a wrong path or a crashing script then lets everything through". לחסימה במקרה כשל: `"onFailure": "block"` (S-003).
- **עובדה:** "use the permission system rather than a hook to enforce a hard allow or deny" (S-003).
- **הסקה:** כללים קריטיים ב-Harness (אבטחה, מניעת פעולות הרסניות) צריכים להיות בהרשאות או ב-Hooks שנכשלים בצורה סגורה, ולא רק בהוראות.

## 2. עלות Context לפי מנגנון

| מנגנון | מתי נטען | עלות | מקור |
|---|---|---|---|
| CLAUDE.md | תחילת סשן, תוכן מלא | בכל בקשה. יעד: פחות מ-200 שורות לקובץ | S-006, S-007 |
| `.claude/rules/` עם `paths` | כשנוגעים בקובץ תואם | רק כשרלוונטי | S-006 |
| Skill | תיאור בתחילת סשן; תוכן מלא כשמופעל | נמוכה. `description` + `when_to_use` נחתכים ב-1,536 תווים | S-001, S-007 |
| Skill עם `disable-model-invocation: true` | רק כשהמשתמש מפעיל | אפס עד להפעלה | S-001, S-007 |
| Subagent | כשמופעל | context נפרד; אזהרה כשסך התיאורים עובר 15,000 טוקנים | S-002, S-007 |
| MCP | שמות כלים בתחילת סשן; schemas לפי צורך (tool search) | נמוכה עד שימוש. אזהרה מעל 10,000 טוקנים של פלט כלי | S-005, S-007 |
| Hook | באירוע | אפס, אלא אם מחזיר פלט | S-007 |
| Plugin מופעל | בכל סשן | שמות ותיאורים של כל ה-Skills וה-Agents שבו נכנסים ל-context בכל turn | S-004 |

- **עובדה:** אחרי compaction, Skills שהופעלו נשמרים עד "the first 5,000 tokens of each", בתקציב משותף של 25,000 טוקנים (S-001).
- **עובדה:** `/context all` מציג כמה טוקנים כל כלי MCP צורך (S-007).
- **הסקה:** לכל רכיב ב-Harness יש עלות קבועה (התיאור שלו) גם כשלא משתמשים בו. יש למדוד את העלות הזו כחלק מההערכה.

## 3. יכולות מובנות שכבר קיימות ב-baseline

- **עובדה:** Subagents מובנים: `Explore` (קריאה בלבד), `Plan` (מחקר במצב תכנון), `general-purpose` (S-002).
- **עובדה:** Skills מובנים: `/code-review`, `/batch`, `/debug` (S-007).
- **עובדה:** Auto memory — הערות ש-Claude כותב בעצמו, נטען בכל סשן (200 השורות הראשונות או 25KB) (S-006).
- **עובדה:** Dynamic workflows — סקריפט ש-Claude כותב ומריץ הרבה subagents, עם אפשרות לאימות צולב של ממצאים (S-007).
- **הסקה:** רכיב חיצוני שמכפיל יכולת מובנת צריך להוכיח שיפור **מעבר** לה. ה-baseline בהשוואה הוא Claude Code עם היכולות המובנות האלה.

## 4. Subagents — בידוד והאצלה

- **עובדה:** "Each subagent starts with a fresh, isolated context window. It doesn't see your conversation history, the skills you've already invoked, or the files Claude has already read." (S-002)
- **עובדה:** Subagent יכול להפעיל subagents עד שלוש שכבות מתחת לשיחה הראשית; עד 20 במקביל כברירת מחדל (S-002).
- **עובדה:** שדות frontmatter רלוונטיים: `tools`, `model`, `permissionMode`, `isolation: worktree`, `memory`, `skills`, `hooks` (S-002).
- **עובדה:** Plugin subagents לא תומכים ב-`hooks`, `mcpServers`, `permissionMode` (S-002).
- **הסקה:** העברת משימה ל-subagent דורשת prompt שעומד בפני עצמו. זו נקודת סיכון לאיבוד מידע (תחום A ו-H).

## 5. שדות לא מוכרים נכשלים בשקט

- **עובדה:** גם ב-Skills וגם ב-Subagents, שדות frontmatter לא מוכרים מתעלמים מהם בלי שגיאה — "misspelled field names fail silently" (S-001, S-002).
- **הסקה:** ה-Harness צריך בדיקה אוטומטית שמאמתת את ה-frontmatter של הרכיבים שלו.

## 6. AGENTS.md

- **עובדה:** Claude Code קורא `AGENTS.md` רק כשאין `CLAUDE.md` בתיקייה הנוכחית או מעליה. כדי להשתמש בשניהם: לייבא את `AGENTS.md` מתוך `CLAUDE.md` (S-006).

## 7. סדר מומלץ לבניית הגדרות

- **עובדה:** התיעוד ממליץ להוסיף מנגנונים לפי טריגרים, למשל: "Claude gets a convention or command wrong twice → Add it to CLAUDE.md"; "You want something to happen every time without asking → Write a hook" (S-007).
- **הסקה:** זה תואם את עקרון "המינימום עם ההשפעה הגדולה ביותר" (שאלה 10 ב-mission.md): להוסיף רכיב רק כשיש בעיה שנצפתה.

## 8. עקרונות כתיבת Skills (S-008)

- תמציתיות: "Default assumption: Claude is already very smart"; גוף `SKILL.md` פחות מ-500 שורות.
- דרגות חופש מותאמות לרגישות המשימה: הוראות כלליות לעבודה פתוחה, סקריפט מדויק לפעולה שבירה.
- הפניות לעומק של רמה אחת בלבד מתוך `SKILL.md`.
- תיאור בגוף שלישי, עם "מה" וגם "מתי".
- לולאות משוב: validator ← תיקון ← חזרה.
- **"Create evaluations BEFORE writing extensive documentation."** ← C-005
