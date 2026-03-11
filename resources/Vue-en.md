# Enterprise-Level Front-End Engineering Specification Documentation - Vue English

## Role: 
Front-End Project Construction

## Task: 
Based on the provided UI design draft images, generate directly runnable Vue3 + Vite front-end code. The code must conform to the "Technology Stack and Specification Requirements" below, with a clear structure, complete comments, and strong maintainability; simultaneously, supplement the UI design draft details and recreate the design draft 1:1 with the UI design draft images, paying attention to details such as fonts, colors, and spacing; and meet the front-end code requirements in the "Output Requirements" below.

## Specifications
1. Framework: Vue 3 (Composable API, prioritize using `<script setup lang="ts">` syntax sugar)
2. Language: TypeScript
3. Build Tool: Vite
4. CSS Solution: Tailwind LESS/Scoped CSS/Element Plus
5. State Management: Pinia (State tree /src/store/index.ts, defining global state such as userInfo, token, etc.)
6. Page Routing: vue-router (Route entry point /src/router/index.ts, dynamically importing specific pages)
7. Component Library: Element Plus
8. API Requests: axios
   - Encapsulate an axios instance /src/api/index.ts, including loading state and exception handling control;
   - Define request /src/api/xxx.ts according to business type, using the encapsulated axios instance to request data, such as specific requests like getList, getDetail, etc.
9. Code Style Guidelines:
   - Follow ESLint + Prettier specification: Use camelCase for variable naming and PascalCase for component naming.
   - Component structure: `<template>` (semantic tag) → `<script setup lang="ts">` (logic) → `<style scoped>` (style)
   - Avoid using `var`, prioritize `const`/`let`; avoid redundant code, extract reusable logic as hooks or utility functions.
   - Use rem/vw units for style, adapting to [mobile/PC], with a base width of [750px/1920px] in the design draft.
10. Performance requirements:
   - Use lazy loading for images, avoid deep style nesting (CSS nesting should not exceed 3 levels).
   - Do not import global styles unless necessary, isolate the scope of component styles.

## Style Details
1. Theme Style
   - Color:
   - Font:
   - Spacing:
   - Rounded corners:
   - Shadow:
2. Interaction Specifications
   - Click:
   - Input:
   - Disable:
   - Loading:
   - Error handling:
   - Success handling:
   - Delete/Remove/Dangerous Behavior:

## Output
1. Code Structure
   ```bash
   src/
   ├── api/ # Interface request configuration
   │ ├── index.ts # Axios instance initialization, request interception, exception handling
   │ ├── goods.ts # Product-related interfaces (e.g., /goods/list)
   │ └── user.ts # User-related interfaces
   ├── assets/ # Static resources
   │ ├── images/ # Image files
   │ └── styles/ # Global styles (e.g., variables.scss, main.css)
   ├── components/ # Common business components (non-page level)
   │ ├── Header.vue # Common header
   │ ├── NavMenu.vue # Navigation menu
   │ └── Common/ # More general atomic components
   ├── constants/ # Constant definitions
   │ ├── routes.ts # Route path constants
   │ └── apiUrls.ts # Interface URL constants
   ├── router/ # Route configuration
   │ └── index.ts # Route entry point (including configurations for /goods/list, etc.)
   ├── store/ # State management (Pinia/Vuex)
   │ ├── index.ts # Store entry point
   │ └── modules/
   │ └── userInfo.ts # User information state
   ├── utils/ # Utility functions
   │ ├── validate.ts # Format validation functions (regular expressions, etc.)
   │ └── request.ts # Axios interceptor encapsulation
   ├── views/ # Page components (corresponding to routes)
   │ ├── goods/
   │ │ └── GoodsList.vue # Product list page
   │ └── login/
   │ └── Login.vue
   ├── App.vue # Root component
   └── main.ts # Entry file (Vue instance, Element Plus import, route mounting)
   ```
2. Output content:
   - Complete .vue file code (including template, script setup, style scoped)
   - Necessary comments (such as component functionality, core logic, parameter descriptions)
   - Dependency description (such as required npm packages: npm install element-plus)
   - Running instructions (such as: npm run dev to start the project)
3. Additional requirements:
   - Code with no syntax errors, can be directly copied and run in a Vue3+Vite project
   - Styles are a 1:1 reproduction of the UI design draft, with no misalignment or missing styles
   - Prioritize the use of native Vue3 features, avoid over-encapsulation