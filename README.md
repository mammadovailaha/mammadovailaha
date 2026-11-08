
esas sehife acilmir

10:24 PM
Build keçdi. Three.js komponenti indi səhifə göstərildikdən sonra yüklənir; brauzerdə WebGL yoxdursa, səhnə atlanır və ana səhifə onsuz açılmalıdır.

Dev server-in 5173 portu istifadə olunurdu, ona görə Vite 5174 portunda başlamışdı. localhost:5173-ü açırsınızsa, terminalda npm run dev işlədərkən göstərilən Local ünvanı istifadə edin.


Edited 2 files
+23
-2
src/Pages/Home/Banner.tsx
src/Pages/Home/
Banner.tsx
+14
-2
src/components/ThreeAccent.tsx
src/components/
ThreeAccent.tsx
+9
-0
10:25 PM
acilir sonra drek her yer ag olur
chunk-ABJ2RQAK.js?v=0bc7cdbf:17987 Download the React DevTools for a better development experience: https://react.dev/link/react-devtools
:5173/node_modules/.…rei.js?v=0bc7cdbf:1  Failed to load resource: the server responded with a status of 504 (Outdated Optimize Dep)
chunk-ABJ2RQAK.js?v=0bc7cdbf:6228 Uncaught TypeError: Failed to fetch dynamically imported module: http://localhost:5173/src/components/ThreeAccent.tsx

10:26 PM
Səbəbi tapdım: Vite @react-three/drei modulunu 504 ilə yükləyə bilmədikdə lazy import tətbiqi boşaldırdı. 3D hissəni error boundary ilə тусгаарлаж, Vite-ə Three.js asılılıqlarını əvvəlчилэн optimize etməyi əlavə etdim. Beləliklə, 3D effekt yüklənməsə də saytın qalan hissəsi açıq qalmalıdır.

Build və lint keçdi. Dəyişikliklərin lokal dev serverdə qüvvəyə minməsi üçün Vite-i dayandırıb yenidən başladın (Ctrl+C, sonra npm run dev) və səhifəni sərt yeniləyin (Ctrl+Shift+R).


Edited 3 files
+34
-2
src/Pages/Home/Banner.tsx
src/Pages/Home/
Banner.tsx
+2
-2
src/components/ThreeAccentBoundary.tsx
src/components/
ThreeAccentBoundary.tsx
+29
-0
vite.config.ts
vite.config.ts
+3
-0
10:27 PM
Download the React DevTools for a better development experience: https://react.dev/link/react-devtools
ThreeAccent.tsx:20  GET http://localhost:5173/node_modules/.vite/deps/@react-three_drei.js?v=df8b83be net::ERR_ABORTED 504 (Outdated Optimize Dep)
ThreeAccentBoundary.tsx:26 TypeError: Failed to fetch dynamically imported module: http://localhost:5173/src/components/ThreeAccent.tsx

The above error occurred in one of your React components.

React will try to recreate this component tree from scratch using the error boundary you provided, ThreeAccentErrorBoundary.

ThreeAccentBoundary.tsx:14 3D hero effect failed to load; keeping the portfolio available. TypeError: Failed to fetch dynamically imported module: http://localhost:5173/src/components/ThreeAccent.tsx
    at Lazy (<anonymous>)
    at Suspense (<anonymous>)
    at ThreeAccentErrorBoundary (http://localhost:5173/src/components/ThreeAccentBoundary.tsx:21:1)
    at ThreeAccentBoundary (<anonymous>)
    at Suspense (<anonymous>)
    at div (<anonymous>)
    at section (<anonymous>)
    at Banner ()
    at div (<anonymous>)
    at Home (<anonymous>)
    at RenderedRoute ()
    at Routes ()
    at AppRouter (<anonymous>)
    at div (<anonymous>)
    at PreferencesProvider ()
    at App (<anonymous>)
    at Router ()
    at BrowserRouter ()

…
10:28 PM
Səbəb köhnə Vite dev server-in köhnəlmiş dependency cache-i: console-da @react-three/drei üçün 504 görünür. Vite konfiqurasiyasında Drei və Three.js üçün dependency pre-optimization təyin etdim, amma artıq işləyən server bunu götürmür.

Köhnə server terminalında Ctrl+C basıb, layihə qovluğunda yenidən başladın:

npm run dev -- --force
Vite-in göstərdiyi Local ünvanı açın və brauzerdə Ctrl+Shift+R edin. Sizdə 5173 və 5174 portları artıq tutulduğu üçün yeni server 5175-də başlaya bilər; terminalda göstərilən ünvanı istifadə edin.

10:28 PM
Download the React DevTools for a better development experience: https://react.dev/link/react-devtools
ThreeAccent.tsx:20  GET http://localhost:5173/node_modules/.vite/deps/@react-three_drei.js?v=5604058b net::ERR_ABORTED 504 (Outdated Optimize Dep)
ThreeAccentBoundary.tsx:26 TypeError: Failed to fetch dynamically imported module: http://localhost:5173/src/components/ThreeAccent.tsx

The above error occurred in one of your React components.

React will try to recreate this component tree from scratch using the error boundary you provided, ThreeAccentErrorBoundary.

ThreeAccentBoundary.tsx:14 3D hero effect failed to load; keeping the portfolio available. TypeError: Failed to fetch dynamically imported module: http://localhost:5173/src/components/ThreeAccent.tsx
    at Lazy (<anonymous>)
    at Suspense (<anonymous>)
    at ThreeAccentErrorBoundary (http://localhost:5173/src/components/ThreeAccentBoundary.tsx:21:1)
    at ThreeAccentBoundary (<anonymous>)
    at Suspense (<anonymous>)
    at div (<anonymous>)
    at section (<anonymous>)
    at Banner ()
    at div (<anonymous>)
    at Home (<anonymous>)
    at RenderedRoute ()
    at Routes ()
    at AppRouter (<anonymous>)
    at div (<anonymous>)
    at PreferencesProvider ()
    at App (<anonymous>)
    at Router ()
    at BrowserRouter ()

…
10:31 PM
@react-three/drei-dən gələn import-u çıxarıb ulduzları Three.js-in öz Points hissəcikləri ilə qurdum. Beləliklə, 504 verən react-three_drei.js faylı artıq lazım deyil.

Dəyişikliyin 5173-də görünməsi üçün əvvəlki Vite serverini Ctrl+C ilə dayandırıb npm run dev -- --force işlədin, sonra brauzerdə Ctrl+Shift+R edin. npm run build və npm run lint keçdi.


Edited ThreeAccent.tsx
+38
-15
10:32 PM
<h1 align="center">👋 Hi there, I'm <span style="color:#f97316;">Ilaha Mammadova</span></h1>

<p align="center">
  🌸 A passionate and detail-oriented <strong>Front-End Developer</strong> who turns creative ideas into beautiful, responsive, and user-focused web experiences.
</p>

💡 About Me
🚀 I’m a self-motivated and growth-oriented developer who loves crafting clean, maintainable, and scalable user interfaces.
💻 I have experience building real-world web projects with modern front-end technologies.
🌱 Currently learning Next.js and Node.js to evolve into a Full-Stack Developer.  

✨ Focus Areas: UI/UX • Component Architecture • Performance • Accessibility  

🧰 Tech Stack
<p align="center">
  <img src="https://skillicons.dev/icons?i=html,css,js,ts,react,tailwind,next,nodejs,git,github,vscode&theme=light" height="45" />
</p>

📈 GitHub Stats
<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=mammadovailaha&show_icons=true&theme=orange&title_color=f97316&icon_color=f97316&text_color=ffffff&bg_color=0d1117" height="160" />
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=mammadovailaha&theme=highcontrast&fire=f97316&ring=f97316&currStreakLabel=f97316" height="160" />
</p>

🪶 My Dev Motto
“Code is not just what you write — it’s how you think.”
<em>– Ilaha Mammadova</em>

📫 Let's Connect
<p align="center">
  <a href="mailto:mammadovailaha03@gmail.com">
    <img src="https://img.shields.io/badge/Email-f97316?style=for-the-badge&logo=gmail&logoColor=white" />
  </a>
  <a href="https://mammadovailahaportfolio.vercel.app/">
    <img src="https://img.shields.io/badge/Portfolio-111111?style=for-the-badge&logo=vercel&logoColor=f97316" />
  </a>
  <a href="https://www.linkedin.com/in/ilaha-mammadova-0ab538356/">
    <img src="https://img.shields.io/badge/LinkedIn-f97316?style=for-the-badge&logo=linkedin&logoColor=white" />
  </a>
  <a href="https://www.instagram.com/ilahahub">
    <img src="https://img.shields.io/badge/Instagram-f97316?style=for-the-badge&logo=instagram&logoColor=white" />
  </a>
</p>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Poppins&weight=600&size=22&pause=1000&color=F97316&center=true&vCenter=true&width=480&lines=Front-End+Developer;React+Enthusiast;Lifelong+Learner;Passionate+about+Clean+UI" alt="Typing SVG" />
</p>
 bu menim githubdaki readme filemdir bunu yenileyek file kimi gonder mene bu portfolio syatina yazdiq e software engineer zad ele
…
11:13 PM
GitHub profiliniz üçün README-ni Software Engineer təqdimatı ilə yenilədim. Portfolio-dakı Avtohesab, Binahesabi və digər layihələri, texnologiyaları, təhsili və əlaqə keçidlərini daxil etdim.

Fayl: README.md


Edited README.md
+66
-69
11:14 PM

































README.md
# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      ...tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      ...tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      ...tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs['recommended-typescript'],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```
README.md
