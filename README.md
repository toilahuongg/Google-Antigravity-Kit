# Google Antigravity Kit

A powerful collection of Agentic Skills and Workflows designed to supercharge your AI coding assistant. This kit provides specialized capabilities for specialized domains including high-end frontend design, 3D graphics, automated documentation, and effective version control.

## 🚀 Features

The kit is organized into **Skills** (specialized capabilities) and **Workflows** (automated processes).

### 🧠 Skills

Located in `.agent/skills`, these provide deep formatted knowledge and tools:

**Frontend & Design**
- **frontend-design**: Create distinctive, production-grade frontend interfaces with high design quality.
- **canvas-design**: Create beautiful visual art and designs.
- **shopify-polaris-design**: Design and implement Shopify Admin interfaces using the Polaris Design System.
- **vercel-react-best-practices**: React and Next.js performance optimization guidelines from Vercel Engineering.

**3D Graphics (Three.js Suite)**
A comprehensive set of skills for building immersive web 3D experiences:
- **Fundamentals**: Scene setup, cameras, and hierarchy (`threejs-fundamentals`).
- **Geometry & Materials**: Shape creation and advanced shading (`threejs-geometry`, `threejs-materials`).
- **Lighting & Textures**: Realistic illumination and texture limits (`threejs-lighting`, `threejs-textures`).
- **Animation & Interaction**: Keyframe animation and user input handling (`threejs-animation`, `threejs-interaction`).
- **Advanced Effects**: Shaders and post-processing (`threejs-shaders`, `threejs-postprocessing`).
- **Asset Loading**: Efficient model and texture loading (`threejs-loaders`).

**Agent Enhancement (Meta-Skills)**
- **skill-creator**: Guide for creating effective new skills.
- **rule-creator**: Create and manage user rules that customize AI behavior.
- **workflow-creator**: Create and manage automated workflows.

**Documentation**
- **docusaurus-generator**: Generate detailed documentation sites using Docusaurus.

### ⚡ Workflows

Located in `.agent/workflows`, these shortcuts automate common tasks:

- **/git-cm**: Commit changes with a descriptive, conventional message.
- **/git-pr**: Create a rigorous Git Pull Request description.
- **/git-sync**: Sync with the remote repository (pull --rebase).
- **/git-undo**: Undo the last commit while keeping changes staged.
- **/readme**: Update this project README based on current project state.

## 📂 Project Structure

```
google-antigravity-kit/
├── .agent/
│   ├── rules/          # User behavior rules
│   ├── skills/         # Capabilities definitions
│   └── workflows/      # Automated process definitions
└── README.md           # This file
```

## 🛠 Usage

This kit is designed to be used by the Agent. The content within `.agent` should be recognized automatically by compatible agentic environments.

To use a workflow, simply type the command (e.g., `git-cm`) in your agent interface.
To use a skill, reference it in your prompt (e.g., "Use threejs to build a spinning cube").

## 📄 License

[Add License Information Here]
