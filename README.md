# Scholar_Monk

# 教师筛选系统项目搭建指南（基于 Node.js + Vite + React + Tailwind + Shadcn UI）

> 本指南详细说明了从安装 Node.js 后，逐步搭建教师筛选系统 Web 项目的完整流程，适用于初学者或团队文档记录。

---

## 📦 1. 安装 Node.js 与初始化项目

### ✅ 安装 Node.js

前往 [https://nodejs.org/](https://nodejs.org/) 下载并安装 LTS 版本。安装完成后在终端验证：

```bash
node -v
npm -v
```

### ✅ 使用 Vite 创建 React 项目

```bash
npm create vite@latest teacher-query --template react
cd teacher-query
npm install
```

---

## 🧱 2. 安装 Tailwind CSS

### ✅ 安装 Tailwind 及其依赖

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

### ✅ 配置 Tailwind (`tailwind.config.js`)

```js
content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
```

### ✅ 初始化 CSS 文件 (`src/index.css`)

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

## 🎨 3. 安装并初始化 Shadcn UI

### ✅ 初始化 Shadcn UI

```bash
npx shadcn-ui@latest init
```

按提示完成以下选项：

- 使用 TypeScript：否（如果你是用 `.jsx`）
- 样式：Default 或 New York
- Base color：slate
- Global CSS 文件路径：`src/index.css`
- 组件路径别名：`@/components`
- 工具函数别名：`@/lib/utils`
- 使用 Server Components：否

---

## 🧩 4. 添加所需 Shadcn UI 组件

```bash
npx shadcn-ui@latest add card
npx shadcn-ui@latest add input
npx shadcn-ui@latest add button
npx shadcn-ui@latest add select
npx shadcn-ui@latest add table
npx shadcn-ui@latest add label
```

如需分页功能：

```bash
npx shadcn-ui@latest add pagination
```

---

## 📁 5. 项目结构建议

```plaintext
teacher-query/
├── src/
│   ├── components/
│   │   └── ui/             # Shadcn UI 组件目录
│   ├── pages/
│   │   └── TeacherQueryPage.jsx
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── tailwind.config.js
├── package.json
```

---

## ⚙️ 6. 编写教师筛选功能页面（TeacherQueryPage.jsx）

### ✅ 包含以下功能模块：

- 使用 `useState` 定义筛选条件和原始教师数据
- 使用 `useEffect` 监听筛选条件变化并执行 `.filter()` 逻辑
- 渲染页面筛选栏和表格数据
- 使用 Shadcn 的 `Card`, `Select`, `Input`, `Button`, `Table` 等组件
- 提供“重置筛选”按钮

### ✅ 示例字段：

```js
const [allTeachers] = useState([
  {
    id: 1,
    university: "复旦大学",
    researchDirection: "嵌入式系统",
    department: "计算机学院",
    teacher: "陈伟男",
    tag: "论文多",
    email: "wnchen@fudan.edu.cn",
    status: "已上线"
  },
  ...
]);
```

---

## 🔗 7. 修改 App.jsx 入口文件

```jsx
import TeacherQueryPage from './pages/TeacherQueryPage';
import './index.css';

function App() {
  return <TeacherQueryPage />;
}

export default App;
```

---

## 🚀 8. 启动项目

```bash
npm run dev
```

浏览器访问： [http://localhost:5173](http://localhost:5173)

---

