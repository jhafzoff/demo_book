To manage a branching strategy with Pull Requests (PRs) for Jupyter Books using `ghp-import`, you can adopt a workflow that involves separating development work from the production-ready build on GitHub Pages. Here's a recommended strategy and a visual diagram.

---

### **Branching Strategy Explanation**

1. **Main Branch** (`main`):
   - This branch holds the source files (Markdown, Jupyter Notebooks, `_toc.yml`, `_config.yml`, etc.).
   - Developers create PRs to `main` to propose changes and improvements to the book content and structure.
   - When PRs are merged into `main`, it triggers the build process.

2. **GitHub Pages Branch** (`gh-pages`):
   - This branch contains the generated HTML files for publishing on GitHub Pages.
   - **Note**: You don’t edit files directly on `gh-pages`. Instead, after building the book from the `main` branch, you use `ghp-import` to push the `_build/html` files to `gh-pages`.

3. **Development Workflow**:
   - Developers work on **feature branches** created off `main` for new content or updates.
   - Once a feature is complete, they create a **Pull Request** (PR) from the feature branch to `main`.
   - After the PR is reviewed and merged, you rebuild the book and publish to `gh-pages` using `ghp-import`.

4. **Publishing Workflow**:
   - After merging changes into `main`, run:
     ```bash
     jupyter-book build mybookname
     ```
   - Then, use `ghp-import` to push the build to `gh-pages`:
     ```bash
     ghp-import -n -p -f _build/html
     ```

---
