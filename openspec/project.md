# Project Context

## Purpose
This is **go-admin-ui**, a Vue.js-based administrative dashboard and management system UI. It serves as the frontend component of the go-admin full-stack application. The system provides:

- **RBAC (Role-Based Access Control)** - Comprehensive permission management system
- **System Administration** - User, role, department, menu, and dictionary management
- **Developer Tools** - Code generation, API documentation (Swagger integration), form builder
- **Monitoring & Logging** - Operation logs, login logs, and server monitoring
- **Content Management** - CMS-like functionality for managing categorized content

This is an enterprise-grade admin template with features like multi-language support, dynamic routing, theme customization, and responsive design.

## Tech Stack

### Core Framework
- **Vue.js 2.6.11** - Progressive JavaScript framework
- **Vue Router 3.4.7** - Official router for Vue.js
- **Vuex 3.5.1** - State management pattern and library

### UI Framework & Components
- **Element UI 2.15.6** - Primary UI component library
- **@riophae/vue-treeselect** - Tree select component
- **vuedraggable 2.24.0** - Drag-and-drop functionality
- **awe-dnd** - Another drag-and-drop library

### Data Visualization
- **ECharts 4.8.0** - Charts and data visualization
- **viser-vue** - Vue visualization components based on G2

### Utilities & Libraries
- **axios 0.21.1** - HTTP client for API requests
- **js-cookie 2.2.1** - Cookie management
- **moment 2.27.0** - Date/time manipulation
- **jszip 3.5.0** - ZIP file creation
- **xlsx 0.16.5** - Excel file operations
- **file-saver 2.0.2** - File saving functionality
- **nprogress 0.2.0** - Progress bar indicator
- **screenfull 5.0.2** - Fullscreen API wrapper
- **clipboard 2.0.6** - Clipboard operations
- **normalize.css 8.0.1** - CSS reset
- **remixicon 2.5.0** - Icon library
- **path-to-regexp 6.1.0** - URL pattern matching
- **fuse.js 6.4.1** - Fuzzy search library
- **vue-count-to 1.0.13** - Count animation component
- **vue-particles 1.0.9** - Particle effects
- **driver.js 0.9.8** - User tour/guide library

### Code Editors
- **codemirror 5.62.0** - Code editor component
- **vue-codemirror 4.0.6** - Vue wrapper for CodeMirror
- **jsonlint 1.6.3** - JSON linting/validation

### Image & Media Handling
- **vue-cropper 0.5.5** - Image cropping
- **dropzone 5.7.2** - File upload component

### Development Tools
- **@vue/cli-service 4.5.13** - Standard tooling for Vue.js development
- **webpack-bundle-analyzer 3.8.0** - Bundle size analysis
- **sass 1.35.1** & **sass-loader 9.0.3** - SCSS/SASS compilation
- **babel-eslint 10.1.0** - ESLint parser for Babel
- **eslint 7.6.0** & **eslint-plugin-vue 6.2.2** - Code linting
- **husky 4.2.5** - Git hooks
- **lint-staged 10.2.11** - Run linters on staged files
- **plop 2.7.4** - Code generator/scaffolding tool
- **mockjs 1.1.0** - Mock data generation

### Build & Optimization
- **compression-webpack-plugin 4.0.0** - Gzip compression for production builds
- **svg-sprite-loader 5.0.0** - SVG sprite generation

### Testing
- **@vue/cli-plugin-unit-jest 4.4.6** - Jest for unit testing
- **@vue/test-utils 1.0.3** - Vue testing utilities

## Project Conventions

### Code Style

#### JavaScript/Vue Style
- **2-space indentation** (enforced by ESLint)
- **Single quotes** for strings (double quotes allowed when needed)
- **No semicolons** (semicolon-free JavaScript style)
- **camelCase** for JavaScript variables and functions
- **PascalCase** for Vue components
- **kebab-case** for Vue component props in templates
- **Const over let** - Use `const` by default, `let` only when reassignment is needed

#### ESLint Configuration
- Extends `plugin:vue/recommended` and `eslint:recommended`
- Parser: `babel-eslint` with ES6 modules
- Enforces `prefer-const` rule
- No trailing whitespace
- Maximum 1 empty line between code blocks
- Vue component name property casing: PascalCase
- Max 10 attributes per line for single-line Vue elements

#### File Organization
- **src/api/** - API service modules organized by feature
- **src/components/** - Reusable Vue components
- **src/views/** - Page-level components organized by route
- **src/layout/** - Layout components (BasicLayout, Navbar, Sidebar, etc.)
- **src/store/** - Vuex store modules
- **src/router/** - Vue Router configuration
- **src/utils/** - Utility functions and helpers
- **src/icons/** - SVG icon assets
- **src/assets/** - Static assets (images, styles, etc.)

#### Import Conventions
- Use `@/` alias for src directory imports
- Order imports: external libraries → internal modules → relative imports
- Group Vue imports at the top of component files

### Architecture Patterns

#### Component Architecture
- **Layout System**: BasicLayout with Sidebar, Navbar, TagsView, and AppMain
- **Scoped Components**: Each view has its own directory with co-located components
- **Reusable Components**: Shared components in `/src/components` directory

#### State Management (Vuex)
- **Modular Store**: Store split into feature-based modules
- **Getters**: Computed properties for store data
- **Actions**: Async operations (API calls)
- **Mutations**: Synchronous state changes

#### Routing
- **Dynamic Routing**: Routes generated from backend API based on user permissions
- **Nested Routes**: Parent-child route relationships for complex views
- **Route Guards**: Permission checks before navigation
- **Lazy Loading**: Components loaded on-demand for better performance

#### API Layer
- **Axios Interceptors**: Request/response interceptors for auth tokens and error handling
- **Service Modules**: API calls organized by feature/domain in `/src/api/`
- **RESTful Conventions**: Follow REST patterns for API endpoints

#### Permission System
- **RBAC Model**: Role-based access control with fine-grained permissions
- **Route-level Permissions**: Routes hidden/show based on user roles
- **Button-level Permissions**: v-permission directive for element-level control
- **Menu Permissions**: Dynamic menu generation based on user permissions

### Testing Strategy

#### Unit Testing
- **Jest**: Test runner and assertion library
- **@vue/test-utils**: Vue component testing utilities
- **Test Location**: Co-located with components or in `__tests__` directories
- **Coverage Goal**: Aim for 80%+ coverage on critical business logic

#### Testing Commands
- `npm run test:unit` - Run unit tests
- `npm run test:ci` - Run lint and unit tests (for CI/CD)

#### Pre-commit Hooks
- **lint-staged**: Runs ESLint on staged `.js` and `.vue` files
- **Auto-fix**: ESLint automatically fixes issues where possible
- **Git Add**: Fixed files are automatically re-staged

### Git Workflow

#### Branching Strategy
- **master** - Main production branch
- **feature/** - Feature branches (e.g., feature/user-management)
- **bugfix/** - Bug fix branches (e.g., bugfix/login-error)
- **hotfix/** - Urgent production fixes

#### Commit Message Conventions
- Conventional Commits format recommended:
  - `feat:` - New features
  - `fix:` - Bug fixes
  - `docs:` - Documentation changes
  - `style:` - Code style changes (formatting, etc.)
  - `refactor:` - Code refactoring
  - `test:` - Adding or updating tests
  - `chore:` - Build process or tooling changes

#### Code Review Process
- ESLint must pass before commits (enforced by husky pre-commit hook)
- Pull requests should include clear description of changes
- Tests should be updated/added for new features

### Development Workflow

#### Environment Setup
- **Node.js**: v8.9+ (engines field in package.json)
- **npm**: v3.0.0+
- **Development Server**: `npm run dev` (runs on port 9527 by default)
- **Production Build**: `npm run build:prod`
- **Staging Build**: `npm run build:stage`
- **Note**: Development scripts use `NODE_OPTIONS=--openssl-legacy-provider` for Node.js compatibility

#### Development Scripts
- `npm run dev` - Start development server with hot-reload
- `npm run lint` - Run ESLint on source files
- `npm run new` - Generate new component/view using Plop
- `npm run svgo` - Optimize SVG icons
- `npm run preview` - Preview production build locally

#### Code Generation
- **Plop**: Interactive scaffolding tool for generating new components
- **Code Generator**: Visual tool for generating CRUD functionality from database tables
- **Form Builder**: Drag-and-drop form/page builder

## Domain Context

### System Modules
1. **User Management** - CRUD operations for system users
2. **Role Management** - Role definition with menu and permission assignment
3. **Menu Management** - Dynamic menu structure with permission labels
4. **Department Management** - Organizational structure (tree-based)
5. **Position Management** - Job positions/titles
6. **Dictionary Management** - System-wide lookup data
7. **Parameter Management** - Runtime system configuration
8. **Operation Log** - Audit trail of user actions
9. **Login Log** - Authentication and access history
10. **API Documentation** - Auto-generated Swagger docs
11. **Code Generation** - Zero-code CRUD generation from tables
12. **Form Builder** - Visual page construction
13. **Server Monitoring** - System resource metrics

### Key Concepts
- **Tenant/Isolation**: System designed for multi-department scenarios
- **Data Permissions**: Role-based data scope (all, custom, department, department+children, self-only)
- **Menu Types**: Directory, menu, and button (for fine-grained control)
- **Permission Labels**: Identify permissions on UI elements (buttons, routes)

## Important Constraints

### Browser Support
- Modern browsers with > 1% market share
- Last 2 versions of major browsers
- IE11+ (with polyfills)

### Performance Requirements
- **Initial Load**: Optimize for fast first contentful paint
- **Bundle Size**: Use code splitting and lazy loading
- **Image Optimization**: Compress images, use WebP when possible
- **Gzip Compression**: Enabled for production builds (files > 10KB)

### Security Requirements
- **JWT Authentication**: Token-based auth with refresh mechanism
- **XSS Prevention**: Avoid v-html with user content, sanitize inputs
- **CSRF Protection**: Token validation on state-changing operations
- **Route Guards**: All protected routes require authentication
- **No Credentials in Code**: Use environment variables for sensitive data

### Environment Constraints
- **Node.js**: Must use v8.9+ (see package.json engines field)
- **npm**: Must use v3.0.0+
- **Backend Dependency**: Requires go-admin backend API (Go/Gin framework)
- **CORS**: Backend must be configured to allow frontend origin
- **OpenSSL Legacy Provider**: Uses `NODE_OPTIONS=--openssl-legacy-provider` for compatibility with newer Node.js versions and older OpenSSL requirements

## External Dependencies

### Backend API
- **go-admin**: Go/Gin-based RESTful API server
- **Base URL**: Configured via environment variables
- **Authentication**: JWT-based token system
- **API Documentation**: Swagger/OpenAPI integration

### Third-party Services
- **Font/Icon Libraries**: Remixicon for UI icons
- **CDN Dependencies**: None (all dependencies bundled)
- **Analytics**: None configured by default

### Build Tools
- **Vue CLI**: Standard Vue.js project scaffolding
- **Webpack**: Module bundler via Vue CLI
- **Babel**: JavaScript transpilation for browser compatibility

### Development Dependencies
- **Git**: Version control (with Husky hooks)
- **Node.js/npm**: Package management and runtime

## Project-specific Notes

### Special Features
- **Dynamic Theme**: Theme picker with color customization
- **Tags View**: Browser-like tab navigation for visited pages
- **Breadcrumb Navigation**: Automatic breadcrumb generation
- **Screenfull**: Fullscreen mode toggle
- **Language**: Primarily Chinese (can be extended for i18n)
- **Error Logging**: Client-side error capture and reporting
- **Drag-and-drop**: Support for sortable lists and grid layouts

### Known Considerations
- Console.log statements allowed in development (disabled in production)
- Debugger statements allowed in development (disabled in production)
- The project follows Vue 2.x patterns (not Vue 3 Composition API)
- Element UI is the primary component library - avoid introducing competing UI frameworks
