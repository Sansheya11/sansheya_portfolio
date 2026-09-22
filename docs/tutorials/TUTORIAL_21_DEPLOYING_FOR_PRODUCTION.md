<img src="../assets/logo.png"> Tutorial 21 – Deploying for production

1. Vite configuration

Open vite.config.js and set the base directory for your application. Since this portfolio is being deployed from the GitHub repository sansheya_portfolio, the base path should match the repository name.

import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
    base: '/sansheya_portfolio/',
    plugins: [react()],
})

In simple terms, your GitHub Pages site will be hosted at:

https://sansheya11.github.io/sansheya_portfolio/

Therefore, the correct Vite base directory is:

base: '/sansheya_portfolio/'

Important: This project uses React, so make sure the Vite configuration uses react() rather than vue().

If you're deploying to Netlify or your own custom domain where your website is located at the root, you can use:

base: '/'

2. Building for production

Before deploying, make sure all dependencies are installed:

npm install

Then compile your project for production:

npm run build

This command packages your React application, assets, and other required files and creates a production-ready version inside the dist folder.

If the build completes successfully, you should see output similar to:

✓ built in ...

Important: If npm run build fails, fix the build error before continuing with deployment.

3. Deploying to GitHub Pages

This project can be deployed using the GitHub Actions workflow included in the .github/workflows folder.

The workflow automatically builds the React/Vite application and deploys the generated files to GitHub Pages.

Before deploying, check the following

Make sure the base directory in vite.config.js matches your repository name:

base: '/sansheya_portfolio/'

Make sure your repository is public if you want the portfolio to be publicly accessible.

Make sure the project is pushed to the correct repository:

https://github.com/Sansheya11/sansheya_portfolio

4. Enable GitHub Actions

Go to:

Your Repository → Settings → Actions → General

Under Actions permissions, select:

Allow all actions and reusable workflows

Then scroll down to Workflow permissions and select:

Read and write permissions

If your workflow requires it, enable:

Allow GitHub Actions to create and approve pull requests

Click Save.

⚠️ If the workflow does not have the required permissions, the deployment may fail after the build stage.

5. Push your changes

After updating vite.config.js and making any other portfolio changes, commit and push them:

git add .
git commit -m "Configure portfolio for GitHub Pages"
git push origin main

Pushing to the repository will trigger the GitHub Actions deployment workflow automatically if the workflow is configured correctly.

6. Check the GitHub Actions deployment

Open your repository on GitHub and go to:

Actions

You should see the portfolio deployment workflow.

If GitHub asks you to enable workflows, select:

I understand my workflows, go ahead and enable them

Then select the deployment workflow and check its status.

If the workflow failed:

Open the failed workflow.

Check the error message.

Fix the issue in your project.

Push the changes again.

If the workflow provides a Re-run jobs option, you can also rerun the failed workflow after correcting the configuration.

7. Configure GitHub Pages

After the GitHub Actions workflow successfully builds and deploys the project, go to:

Your Repository → Settings → Pages

Under Build and deployment, set:

Source: Deploy from a branch

Branch: gh-pages

Folder: / (root)

Click Save.

If your GitHub Actions workflow uses GitHub's newer Pages deployment method (actions/deploy-pages), GitHub Pages may instead be configured with Source: GitHub Actions. Follow the source setting used by your workflow. Do not create a second deployment method unnecessarily.

8. Your live portfolio

Once GitHub finishes processing the deployment, your portfolio will be available at:

https://sansheya11.github.io/sansheya_portfolio/

You can also find the live deployment from your repository's Deployments section.

Resume link

Once the portfolio is working, use this link on your resume:

https://sansheya11.github.io/sansheya_portfolio/

For a cleaner resume header, you can display it as:

Portfolio | GitHub | LinkedIn

9. Updating the portfolio later

Whenever you make changes to your portfolio:

git add .
git commit -m "Update portfolio"
git push origin main

GitHub Actions will automatically build and deploy the latest version if the workflow is configured correctly.

Next Steps

Ready to keep going? Check out the next bonus tutorial or revisit the previous one if you need a refresher:

⬅️ Previous: ArticleContactForm

      |      

Next: Bonus - Creating Your Own Custom Article ➡️