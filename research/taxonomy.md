# טקסונומיה

שני צירי סיווג נפרדים (ראו CLAUDE.md, סעיף 6).

---

## ציר 1 — סוגי רכיבים

מה הרכיב **טכנית**. ההגדרות של Skill, Agent, Hook ו-MCP אומתו מול התיעוד הרשמי (מנה 1).

| ערך | הגדרה | מקור | סטטוס |
|---|---|---|---|
| `Skill` | תיקייה עם `SKILL.md` (YAML frontmatter + הוראות Markdown) וקבצים נלווים. התיאור נטען ל-context בכל סשן; התוכן המלא נטען רק כשה-Skill מופעל — על ידי Claude לפי התאמה לתיאור, או על ידי המשתמש ב-`/name`. Slash commands מוזגו לתוך Skills | S-001, S-007 | אומת |
| `Agent` | Subagent: קובץ Markdown עם frontmatter, שגופו הוא ה-system prompt. רץ ב-context window נפרד, בלי היסטוריית השיחה, עם כלים והרשאות משלו, ומחזיר סיכום | S-002, S-007 | אומת |
| `Hook` | handler שה-harness מריץ אוטומטית באירוע במחזור החיים (למשל `PreToolUse`, `Stop`). חמישה סוגים: `command`, `http`, `mcp_tool`, `prompt`, `agent`. דטרמיניסטי — רץ בלי ש-Claude מחליט | S-003, S-007 | אומת |
| `MCP` | שרת Model Context Protocol שחושף ל-Claude כלים ונתונים של מערכת חיצונית (tools / prompts / resources) | S-005, S-007 | אומת |
| `CLI` | כלי שורת פקודה ש-Claude מפעיל דרך Bash | הגדרת הפרויקט | הוגדר |
| `Framework` | מערכת או אוסף שמשלב כמה סוגי רכיבים | הגדרת הפרויקט | הוגדר |
| `Tool` | תוכנה או שירות מחוץ ל-Claude Code | הגדרת הפרויקט | הוגדר |
| `Methodology` | שיטת עבודה או פרקטיקה הנדסית, ללא מימוש תוכנה מחייב | הגדרת הפרויקט | הוגדר |
| `Instructions` | קובץ הוראות קבוע שנטען ל-context בלי הפעלה מפורשת: CLAUDE.md, `.claude/rules/`, AGENTS.md, output style, סט כללים (למשל Cursor rules) | S-006, S-007; החלטה 2026-11-16 (G-003) | הוגדר |

### מקרי גבול

| מקרה | מה זה לפי התיעוד | כלל סיווג בפרויקט |
|---|---|---|
| Plugin | "שכבת האריזה": תיקייה עם manifest שמאגדת Skills, Agents, Hooks ושרתי MCP ליחידה אחת שמותקנת מ-marketplace (S-004, S-007) | Plugin אינו סוג רכיב. Plugin שמאגד כמה סוגים נרשם כ-`Framework`, וכל רכיב בתוכו נרשם בנפרד עם `parent_component` |
| Slash command (`.claude/commands/`) | "Custom commands have been merged into skills" (S-001) | נרשם כ-`Skill` |
| Skill עם `context: fork` | Skill שרץ בתוך Subagent (S-001) | נרשם כ-`Skill`, עם הערה בשדה `how_it_works` |
| CLAUDE.md, `.claude/rules/`, AGENTS.md | קובצי הוראות שנטענים בתחילת סשן או לפי נתיב (S-006) | נרשם כ-`Instructions` |
| Output style | הוראות לתפקיד, טון ופורמט לכל הסשן (S-007) | נרשם כ-`Instructions` |
| יכולות מובנות (Explore, Plan, `/code-review`, `/debug`, `/batch`, auto memory, dynamic workflows) | חלק מ-Claude Code עצמו (S-002, S-007) | לא נרשמות כרכיבים. הן חלק מה-baseline, ומתועדות ב-`references/documentation/claude-code-extension-mechanisms.md` |

---

## ציר 2 — תחומים וקטגוריות

**הקטגוריות נגזרות מהמחקר** (שלב 4) ואינן נקבעות מראש. יעד: 8–12 קטגוריות עליונות, בלי לכפות את המספר.

תחומי הפתיחה מ-`mission.md` (סעיף 5) הם נקודת מוצא לחיפוש בלבד.

### אחריויות חוזרות שזוהו

| אחריות | רכיבים | מנה |
|---|---|---|
| פיתוח ושיפור Skills עם הערכה מול baseline | C-001, C-005 | 1 |
| בדיקות E2E לאפליקציות ווב | C-002 | 1 |
| בניית שרתי MCP | C-003 | 1 |
| עידוד המשתמש לבדוק תשובות לפני פעולה | C-004 | 1 |

### קטגוריות עליונות
<!-- ממולא בשלב 4 -->

### רכיבים חוצי-תחומים
<!-- ממולא בשלב 4 -->
