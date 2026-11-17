# Developer landing page

A short English/Arabic page, built with plain HTML and CSS. No build step,
JavaScript, external fonts, or analytics.

## Preview locally

From this directory, run:

```sh
php -S 127.0.0.1:8000 -t site
```

Open <http://127.0.0.1:8000>. Stop the server with Ctrl+C.
Edit the text in [site/index.html](site/index.html) and the appearance in
[site/styles.css](site/styles.css).

## Contact form

The form is enabled and uses the Formspree endpoint configured in
[site/index.html](site/index.html). To change the receiving form:

1. Create a form at [Formspree](https://formspree.io/), verify your receiving
   email, and copy its endpoint, such as `https://formspree.io/f/YOUR_FORM_ID`.
   The endpoint ID is public; do not put your receiving email or account
   credentials in the HTML.
2. In [site/index.html](site/index.html):
   - Replace the `<form>` element's `action` URL with your actual endpoint.
3. Keep the hidden `_gotcha` field. Formspree documents this
   [honeypot filter](https://help.formspree.io/articles/building-your-form/honeypot-spam-filtering/)
   and its built-in reCAPTCHA protection. Keep provider-side spam protection
   enabled; review the account's current settings and plan limits. Enable
   domain restrictions if your plan supports them, including your actual
   Pages or custom domain.
4. Preview the enabled form. Check required fields and email validation, then
   send a test message you authorize. Confirm the provider's submission result,
   actual delivery, and that replying reaches the sender.

Submissions use a normal HTML POST and navigate to Formspree's hosted response,
which may include a CAPTCHA. There is no local success message or custom
backend. Your visitors' name, reply email, and message are processed by
Formspree; review its privacy terms before enabling the form. Browser checks
and honeypots cannot prevent all spam, and an endpoint remains public.

## Publish on GitHub Pages

This site uses [abumosaab/abumosaab.github.io](https://github.com/abumosaab/abumosaab.github.io)
and publishes to <https://abumosaab.github.io/>. Push changes to `main` to deploy
using GitHub Actions.

For a different repository:

1. Create a GitHub repository and push this directory to its default branch.
   Include the hidden `.github` directory.
2. In the repository, open **Settings > Pages > Build and deployment**.
   Choose **GitHub Actions** as the source.
3. In **Actions**, select **Deploy to GitHub Pages**, then **Run workflow**
   on the default branch. Future pushes to that branch deploy automatically.
4. Open the URL shown by the deployment. Check both languages, mobile layout,
   and the configured contact form.

The [workflow](.github/workflows/deploy.yml) uses the repository's actual default
branch, so it works with `main` or another default branch name. Runs on other
branches skip deployment. If environment protection is configured, allow the
default branch to deploy to `github-pages`.

Only [site/](site/) is uploaded. Relative asset URLs support both
`https://USERNAME.github.io/` and `https://USERNAME.github.io/REPOSITORY/`.
No secrets are required by the workflow. Live deployment and message delivery
must be verified after repository and Formspree setup.
