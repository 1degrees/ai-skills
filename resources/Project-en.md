## Role
You are a System Architect

## Task List
1. Read the XXX file in this folder and complete the system requirements analysis based on the file content.
2. Based on the requirements analysis, design and create the system database table structure, and develop and start the system's front-end and back-end projects.
3. The project directory is divided into front-end and back-end.
4. Front-end architecture must meet front-end specifications.
5. Back-end architecture must meet back-end specifications.

## Front-end Specifications

### Technology Stack Selection
1. Framework: React 18+
2. Language: TypeScript
3. Build Tool: Vite
4. CSS Solution: Tailwind Less/Scoped
5. State Management: React Context API (State tree /src/context/index.ts, defining global state, such as: userInfo, token, etc.)
6. Page Routing: React Router DOM
7. Component Library: Antd-design
8. API Requests: Axios
   - Encapsulate an axios instance /src/services/index.ts, including loading status and exception handling control;
   - Define requests /src/services/xxx.ts according to business type, using the encapsulated axios instance to request data, such as getList, getDetail, etc.

9. Code Style Guidelines:
   - Follow ESLint + Prettier specification: Use camelCase for variable naming and PascalCase for component naming.
   - Prohibit the use of `var`, prioritize `const`/`let`; avoid redundant code, extract reusable logic as hooks or utility functions.
   - Use rem/vw units for style design, adapting to [mobile/PC], with a base width of [750px/1920px] in the design draft.

10. Performance Requirements:
   - Use lazy loading for images, avoid deep style nesting (CSS nesting should not exceed 3 levels).
   - Do not import global styles unless necessary, and isolate the scope of component styles.

### Style Interaction Style
1. Theme Style
   - Colors: Primary color: #1890FF; Neutral color: #F5F5F5; Success: #52C41A; Error: #FF4D4F; Failure: #FF4D4F; Warning: #FAAD14
   - Font: Font: Square font; Size: 14px; Color: #333333
   - Spacing: Large: 12px Medium: 8px Small: 4px
   - Rounded corners:
   - Shadow:

2. Interaction Guidelines
   - Click:
   - Disable:
   - Loading:
   - Error handling:
   - Success handling:
   - Delete/Remove/Dangerous behavior:

### Output Structure Guidelines
1. Code Structure and Directory Guidelines
   ```bash
   src/
   ├── assets/ # Static resources (images, global fonts, SVG, etc.)
   ├── components/ # Globally shared common UI components (Button, Input, Modal)
   │ └── Button/
   │ ├── Button.tsx
   │ ├── Button.module.css
   │ └── index.ts # Export entry point, convenient for import { Button } from '@/components'
   ├── config/ # Global configuration (API Endpoints, constants, ... (Enumeration)
   ├── features/ # Core business logic (divided by functional modules) ⭐ Recommended practice
   │ ├── auth/ # Login/registration related
   │ │ ├── components/ # Components for auth only
   │ │ ├── hooks/ # auth-specific hooks
   │ │ ├── services/ # auth-related API requests
   │ │ └── types.ts # Type definitions
   │ └── dashboard/ # Dashboard related
   ├── hooks/ # Globally reusable custom hooks (e.g., useDebounce, useLocalStorage)
   ├── layouts/ # Page layout components (MainLayout, AdminLayout)
   ├── pages/ # Routing pages (usually only responsible for assembling components in features)
   ├── services/ # Global API client configuration (Axios instance, interceptors)
   ├── store/ # State management (Redux slices, Zustand stores)
   ├── types/ # Global generic TypeScript type definitions
   └── utils/ # Pure utility functions (date formatting, validation, etc.)
   ```
2. Output Content:
   - Complete .tsx file code (including interaction logic and render)
   - Necessary comments (such as component functionality, core logic, and parameter descriptions)
   - Dependency descriptions (e.g., required npm packages: `npm install antd-design`)
   - Running instructions (e.g., `npm run dev` to start the project)

3. Additional Requirements:
   - Code with no syntax errors, can be directly copied and run in a React project
   - Styles are a 1:1 reproduction of the UI design draft, with no misalignment or missing styles
   - Prioritize native Vue 3 features and avoid over-encapsulation

## Backend Specifications
### Technology Stack Selection
1. Framework: Spring Boot 3+
2. Language: Java 17
3. Database: MySQL 8.0+ (user: root password: Root@123456)
4. Database connection pool: MyBatis, MyBatis-Plus
5. Interface documentation: Swagger 2.0
6. Build tool: Maven
7. Deployment environment: Docker
8. Service registration and discovery: Nacos 2.2.3
9. Message queue: Kafka 2.8.1

### Output structure specification
1. Core directory structure
   ```bash
   src/main/java/com/yourcompany/projectname
   ├── common/ # Common modules
   │ ├── annotation/ # Custom annotations
   │ ├── config/ # Global configuration (e.g., Swagger, MyBatisPlusConfig)
   │ ├── constant/ # Constant enumeration
   │ ├── exception/ # Exception definition and global exception handler
   │ └── result/ # Unified Return Result Encapsulation (R.java)
   ├── controller/ # Interface Layer (RESTful API)
   ├── domain/ # Data Model
   │ ├── dto/ # Front-end Transmission Object (Receives Parameters)
   │ ├── entity/ # Database Entity Class (Corresponds to MySQL Tables)
   │ └── vo/ # View Object (Returns Data to the Front-end)
   ├── mapper/ # MyBatis/MyBatis-Plus Persistence Layer Interface
   ├── service/ # Business Logic Interface Layer
   │ └── impl/ # Business Logic Implementation Layer
   ├── listener/ # Kafka Message Listener
   ├── manager/ # General Business Processing Layer (Optional, handles third-party SDKs or cross-service combinations)
   └── utils/ # Utility Classes (Date, String, Encryption)
   ```

2. Resource File Structure (src/main/resources)
   ```bash
   resources/
   ├── mapper/ # MyBatis XML mapping file
   ├── application.yml # Main configuration file (including Nacos connection address)
   ├── application-dev.yml # Development environment configuration (MySQL: root/Root@123456)
   ├── application-prod.yml # Production environment configuration
   └── logback-spring.xml # Log configuration
   ```