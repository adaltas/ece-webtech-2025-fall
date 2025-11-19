
# Project Instructions

The goal of this project is to design and develop a complete web application based on the stack we studied this semester (Next.js, Supabase, Tailwind).

**You have total freedom over the topic**. You are building a product. It could be a blogging platform, a crypto portfolio tracker, a cooking recipe manager, an e-commerce dashboard, a travel journal, or a workout tracker.

## Requirements

While the subject is yours to choose, every application MUST meet the following technical constraints to constitute a Minimum Viable Product (MVP):

- **Next.js App Router**: You must use the latest Next.js features (Server Components, Layouts, Loading UI).
- **Supabase Integration**: You must use Supabase for Authentication and Database.
- **Security First**: Data must be protected. A user should never be able to edit another user's data (Row Level Security).
- **Tailwind CSS**: All styling must be done via Tailwind.

Bonus tasks are exempt from these restrictions.

> [!CAUTION]
> Those requirements are strict. Failing to meet any of them will result in a failing grade.

## Evaluation criteria

The evaluation will be conducted via an oral presentation (Demo + Q&A) and a review of your source code. You will be graded on the following criteria:

### 1. Concept & User Experience (20%)

Does the app look and feel like a real product?

- **UI/UX**: The interface is intuitive, responsive (mobile-friendly), and visually consistent.
- **Navigation**: Users can easily move between pages (Home, Profile, Details, 404 pages).
- **Polish**: Loading states are handled (skeletons/spinners), errors are displayed gracefully (not just console.log), and the app feels fast.

### 2. Full-Stack Functionality (40%)

Does the app actually work?

- **Authentication flow**: Users can Sign Up, Sign In (GitHub/OAuth preferred), and Sign Out. The UI updates to reflect the user's state.
- **CRUD operations**: You must implement Create, Read, Update, and Delete operations for at least one major resource (e.g., Articles, Recipes, Tasks).
- **Data relationships**: At least one relationship between tables (e.g., Users and Posts, Posts and Comments).
- **Search/Filtering**: Users can search and/or filter the main resource list (e.g., search posts by title, filter tasks by status).
- **Use of external API**: The app consumes data from at least one external public API (e.g., fetching weather data, news articles, or stock prices).

### 3. Engineering & Architecture (20%)

Is the code clean and secure?

- **Next.js usage**: Correct distinction between Server Components (fetching data) and Client Components (interactivity). Proper use of layout.tsx.
- **Security (RLS)**: Row Level Security policies are correctly configured in Supabase. You cannot fetch/edit data you don't own (unless intended, like public posts).
- **Data fetching**: Data is fetched efficiently.

### 4. Project Management & Quality (20%)

Is the repository professional?

- **Git history**: Clean commit history using Conventional Commits.
- **Documentation**: A README.md that explains what the project is, how to run it locally, and a brief self-evaluation.
- **Code style**: Consistent formatting, meaningful variable names, and file structure (components are organized).

> [!CAUTION]
> Grades are given to the group as a whole. All members must contribute equally. Any insufficient contribution may lead to a failing grade for the individual.

## Deliverables

1. **Source Code**: A private GitHub repository (invite your instructor).
2. **Live URL**: The app must be deployed on <Vercel.com> and <Supabase.com>.
3. **README.md**: Must include:

   - Project Name & Pitch (1 sentence).
   - Tech Stack summary.
   - Prerequisites and instructions to run locally.
   - User Guide to use the application.

4. **PROJECT.md**: Include self-evaluation on each item. A template is provided in PROJECT.md.

## The Oral Presentation (15 mins)

You will demo your application live. Be prepared to:

1. **Pitch**: Explain your concept in 30 seconds.
2. **Demo**: Walk through the "Happy Path" (Sign up → Create content → Interact).
3. **Technical QA**: The instructor will ask to see specific code snippets (e.g., "Show me your RLS policies" or "Show me how you fetch this list").

## Bonus

Outstanding features (e.g., responsive design, 3D animations, AI integration) can award up to +4 bonus points.

> [!TIP]  
> +0.5 point will be given to students who provide an honest feedback about their learning experience during the course (e.g., what they found useful, what could be improved, etc.). This feedback can be included in the PROJECT.md file or sent directly to the instructor via email.
