# Claude Code Harness — פרויקט מחקר

## מטרה
לחקור את האקוסיסטם סביב Claude Code ולבנות בהמשך **AI Software Engineering Harness** איכותי: שילוב מבוקר של Skills, Agents, Hooks, שרתי MCP, כלים ותהליכי עבודה, שמשפר באופן מדיד את איכות הנדסת התוכנה לעומת Claude Code ללא Harness.

יעד נוסף: מתודולוגיית פיתוח שמנוהלת על ידי סוכנים — הסוכנים מנהלים את התהליך, שומרים ומעדכנים את הידע ומבצעים את העבודה, והאדם נדרש רק לקבלת החלטות ולסקירה.

המטרה איננה ה-Harness הגדול ביותר, אלא האפקטיבי ביותר.

## מסמכי יסוד
- [research/mission.md](research/mission.md) — משימת המחקר המלאה: מקורות, תחומים, תוצרים ושאלות.
- [CLAUDE.md](CLAUDE.md) — כללי העבודה המחייבים.

## מתודולוגיה בקצרה
- גילוי לרוחב לפני סיווג; הטקסונומיה נגזרת מהממצאים.
- חילוץ רכיבים בודדים מתוך ריפואים, לא רק הערכת ריפואים שלמים.
- מקורות מקוריים, אימות טענות, וסימון מפורש של מידע לא ידוע.
- קריאה מהווב בלבד, בלי שכפול ריפואים ובלי התקנות.
- עבודה במנות, עם תיעוד ב-[research-log.md](research/research-log.md).

## שלבי הפרויקט

| # | שלב | תוצר עיקרי | סטטוס |
|---|---|---|---|
| 0 | הקמת סביבת המחקר | מבנה, כללים, מסמך משימה | הושלם |
| 1 | מקורות פתיחה | `sources.md` | בתהליך |
| 2 | חילוץ רכיבים | `components.csv` | טרם התחיל |
| 3 | הרחבת גילוי | `sources.md`, `people-and-organizations.md` | טרם התחיל |
| 4 | סיווג | `taxonomy.md` | טרם התחיל |
| 5 | ניתוח תחומים | `domain-analysis/` | טרם התחיל |
| 6 | ניתוח כיסוי | `research-gaps.md` | טרם התחיל |
| 7 | המלצות ראשוניות | `integration-candidates.md` | טרם התחיל |
| 8 | מדידת Baseline | `benchmarks/baseline/` | טרם התחיל |
| 9 | בניית ה-Harness ומדידתו | `benchmarks/harness/` | טרם התחיל |

שלבים 1–7 הם מחקר בלבד. שלבים 8–9 יתחילו רק אחרי החלטה מפורשת.

## תוכנית מנות (שלבים 1–2)

| מנה | תוכן | סטטוס |
|---|---|---|
| 1 | תיעוד רשמי של Claude Code ו-`anthropics/skills` — אימות הגדרות סוגי הרכיבים | טרם התחיל |
| 2 | Superpowers, Matt Pocock Skills | טרם התחיל |
| 3 | Spec Kit, BMAD Method, GSD | טרם התחיל |
| 4 | Aider, Cline, Roo Code, AGENTS.md | טרם התחיל |
| 5 | קטלוגים: Awesome Cursor Rules, Awesome Claude Skills, Awesome Context Engineering | טרם התחיל |
| 6 | הערכה ו-Benchmarking | טרם התחיל |
| 7 | אבטחה | טרם התחיל |
| 8 | בדיקות והנדסת איכות | טרם התחיל |
| 9 | ארכיטקטורה ואיכות תכנון | טרם התחיל |
| 10 | Observability, ביצועים ו-Tracing של סוכנים | טרם התחיל |

## ניווט

```text
claude-code-harness/
├── README.md                     # קובץ זה
├── CLAUDE.md                     # כללי עבודה
├── research/
│   ├── mission.md                # משימת המחקר
│   ├── sources.md                # רישום מקורות שנבדקו
│   ├── components.csv            # מלאי רכיבים
│   ├── taxonomy.md               # סוגי רכיבים וקטגוריות
│   ├── people-and-organizations.md
│   ├── evaluation-framework.md   # שדות, קריטריונים ומתודולוגיית השוואה
│   ├── integration-candidates.md
│   ├── research-gaps.md
│   ├── research-log.md
│   └── domain-analysis/          # ניתוח לכל תחום
├── references/                   # קטעים רלוונטיים ממקורות
│   ├── repositories/
│   ├── articles/
│   └── documentation/
└── benchmarks/
    ├── baseline/                 # Claude Code ללא Harness
    └── harness/                  # Claude Code עם Harness
```
