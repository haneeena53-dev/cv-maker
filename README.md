# cv-maker


A lightweight, frontend-only web app for building a clean, A4-ready resume in the browser. Fill in a form, watch the resume update live, and export it as a PDF with one click. Everything runs locally: no backend, no sign-up, no data leaves your device.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

**Live demo:** https://YOUR-USERNAME.github.io/resume-builder/

---

## Table of Contents

- [Features](#features)
- [Screenshot](#screenshot)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Project Structure](#project-structure)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [نبذة بالعربية](#نبذة-بالعربية)

## Features

- **Live preview.** The resume re-renders on every keystroke.
- **PDF export.** Exports only the resume, on A4, using `html2pdf.js`.
- **Bilingual output.** Switch the resume between English (LTR) and Arabic (RTL), including headings and text direction.
- **Structured sections.** Contact line, Professional Summary, Education, Projects, Internships & Training, Technical Skills, Key Competencies, and Languages.
- **Repeatable entries.** Add or remove any number of education items, projects, trainings, skill categories, and languages.
- **Tag-style competencies.** Press `Enter` or `,` to add an item, or paste a comma-separated list.
- **Responsive layout.** Side by side on desktop, stacked on mobile, with the A4 preview scaling to fit.
- **Private by design.** No storage and no server. The only network requests load the PDF library and the font.
- **Empty by default.** The form starts blank, and a "Clear all" button resets it.



Notes:

- In multi-line fields, write one bullet per line.
- Empty fields and empty sections are omitted from the output.
- Long resumes paginate automatically, but a single page gives the cleanest result.

## Tech Stack

| Layer | Technology |
|---|---|
| Structure | HTML5 |
| Styling | CSS3 (Grid, Flexbox, custom properties) |
| Logic | Vanilla JavaScript (ES6), no framework, no build step |
| PDF export | [html2pdf.js](https://github.com/eKoopmans/html2pdf.js) via CDN |
| Typography | [Cairo](https://fonts.google.com/specimen/Cairo) via Google Fonts |

## Architecture

```
Form fields  --input events-->  State object  --render()-->  Live preview
                                                                  |
                                              clone at fixed A4 width (off-screen)
                                                                  |
                                                            html2pdf -> PDF
```

- A single `state` object is the source of truth. Each input updates it and triggers a re-render.
- All user-provided text is HTML-escaped before it is rendered.
- For export, the preview is cloned off-screen at a fixed A4 width, so the PDF output is independent of screen size and preview scaling.

## Project Structure

```
resume-builder/
├── index.html    # HTML, CSS and JavaScript in a single file
└── README.md
```

## Roadmap

- [ ] Save and restore drafts with `localStorage` (opt-in)
- [ ] Multiple templates and accent colors
- [ ] Import and export data as JSON
- [ ] Optional profile photo
- [ ] Drag-and-drop section reordering
- [ ] Offline support by bundling the PDF library

## Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push the branch: `git push origin feature/your-feature`
5. Open a pull request.

For bugs and feature requests, please open an issue.

## License

Released under the [MIT License](LICENSE).

---

# نبذة بالعربية

**منشئ السيرة الذاتية** تطبيق ويب بسيط يعمل بالكامل داخل المتصفح دون خادم أو تسجيل دخول. تملئين النموذج
فتظهر السيرة الذاتية أمامك لحظة بلحظة، ثم تنزّلينها بملف PDF بحجم A4 بضغطة واحدة.

**المميزات**

- معاينة حية تتحدث مع كل حرف.
- تصدير السيرة الذاتية فقط إلى PDF بجودة عالية.
- سيرة بالإنجليزية أو بالعربية مع دعم الكتابة من اليمين إلى اليسار.
- أقسام كاملة: الملخص المهني، التعليم، المشاريع، التدريب، المهارات التقنية، الكفاءات، اللغات
