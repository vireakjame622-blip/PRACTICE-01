# Exercise 1: CSS Flexbox Top-to-Bottom Strategy (Google Classroom Mockup)

## 1. Top-to-Bottom Decomposition Overview

Following the **Top-to-Bottom approach**, we first identify the primary global containers, then proceed inward into sub-containers, and finally reach the atomic item components.

```text
.page-container (direction: column, min-height: 100vh)
│
├── 1. .navbar (direction: row, justify-content: space-between, flex: 0)
│   ├── .navbar-left (direction: row, align-items: center)
│   │   ├── .menu-icon
│   │   └── .class-name ("HTML 2023 C")
│   ├── .navbar-center (direction: row, justify-content: center)
│   │   └── .nav-tabs ("Stream", "Classwork", "People", "Grades")
│   └── .navbar-right (direction: row, align-items: center)
│       └── .nav-actions (apps, settings, profile avatar)
│
└── 2. .main-container (direction: column, flex: 1, width: 85%, margin: auto)
    │
    ├── 2.1 .class-banner (direction: row, justify-content: space-between, align-items: flex-end)
    │   ├── .banner-title ("HTML 2023 C")
    │   └── .banner-customize-btn ("Customize" button)
    │
    └── 2.2 .content-layout (direction: row, align-items: flex-start, gap: 24px)
        │
        ├── 2.2.1 .sidebar (direction: column, flex: 0 0 240px, gap: 16px)
        │   ├── .card-meet (direction: column)
        │   │   ├── .card-header (row: icon + "Meet" + menu)
        │   │   └── .card-btn ("Generate link")
        │   ├── .card-class-code (direction: column)
        │   │   ├── .card-header (row: "Class code" + menu)
        │   │   └── .code-display (row: "ai2pvt3" + expand icon)
        │   └── .card-upcoming (direction: column)
        │       ├── .upcoming-title ("Upcoming")
        │       ├── .upcoming-due-items
        │       └── .upcoming-view-all-link ("View all")
        │
        └── 2.2.2 .stream-content (direction: column, flex: 1, gap: 16px)
            ├── .announcement-card (direction: row, align-items: center, justify-content: space-between)
            │   ├── .announcement-left (direction: row, align-items: center, gap: 12px)
            │   │   ├── .user-avatar
            │   │   └── .announcement-placeholder ("Announce something to your class")
            │   └── .announcement-actions (re-use icon)
            │
            └── .assignment-card (direction: row, justify-content: space-between, align-items: center)
                ├── .assignment-left (direction: row, align-items: center, gap: 16px)
                │   ├── .assignment-icon (clipboard icon in blue circle)
                │   └── .assignment-text (direction: column, gap: 4px)
                │       ├── .assignment-title ("Teacher posted a new assignment...")
                │       └── .assignment-date ("Jul 8")
                └── .assignment-menu (more vertical options icon)
```

---

## 2. Flex Containers Specifications Table

| Level | Container Name | Flex Direction | Flex Value | Alignment & Justification | Description |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Root** | `.page-container` | `column` | `min-height: 100vh` | `width: 100%` | Outermost container wrapping navbar and main content |
| **Top** | `.navbar` | `row` | `flex: 0` | `justify-content: space-between; align-items: center;` | Header bar with title, tabs, and action icons |
| **Top** | `.main-container` | `column` | `flex: 1` | `width: 85%; margin: 24px auto;` | Main body container holding banner and content columns |
| **Section** | `.class-banner` | `row` | `flex: 0` | `justify-content: space-between; align-items: flex-end;` | Large hero image with class title and customize button |
| **Section** | `.content-layout` | `row` | `flex: 1` | `align-items: flex-start; gap: 24px;` | 2-column layout holding sidebar and stream content |
| **Column** | `.sidebar` | `column` | `flex: 0 0 240px` | `gap: 16px;` | Left column for Meet, Class Code, and Upcoming cards |
| **Column** | `.stream-content` | `column` | `flex: 1` | `gap: 16px;` | Right column containing announcement box and assignment cards |
| **Component** | `.announcement-card` | `row` | `flex: 0` | `justify-content: space-between; align-items: center;` | Card allowing teacher/student to post an announcement |
| **Component** | `.assignment-card` | `row` | `flex: 0` | `justify-content: space-between; align-items: center;` | Post item for assignments with icon, details, and menu |

---

## 3. CSS Flex Rules Summary

```css
/* 1. Page Shell */
.page-container {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

/* 2. Top Navigation Bar */
.navbar {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 10px 24px;
}

.navbar-left,
.navbar-center,
.navbar-right {
    display: flex;
    flex-direction: row;
    align-items: center;
}

/* 3. Main Container */
.main-container {
    display: flex;
    flex-direction: column;
    width: 85%;
    margin: 24px auto;
    gap: 24px;
}

/* 4. Hero Banner */
.class-banner {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: flex-end;
    padding: 24px;
}

/* 5. Content Layout (2 Columns) */
.content-layout {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    gap: 24px;
}

/* 6. Sidebar (Fixed width column) */
.sidebar {
    display: flex;
    flex-direction: column;
    flex: 0 0 240px;
    gap: 16px;
}

/* 7. Stream Content (Flexible fluid column) */
.stream-content {
    display: flex;
    flex-direction: column;
    flex: 1;
    gap: 16px;
}

/* 8. Announcement & Assignment Cards */
.announcement-card,
.assignment-card {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 16px;
}

.assignment-left {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 16px;
}

.assignment-text {
    display: flex;
    flex-direction: column;
    gap: 4px;
}
```

