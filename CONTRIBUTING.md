## Scope

This Github repository exists to discuss and solve problems directly related to the project. 

* [Shopify Development](https://shopify.dev/themes)
* [Shopify Help Center](https://help.shopify.com/themes)
* [Shopify Forum](https://ecommerce.shopify.com/forums)
* [Shopify Experts](https://experts.shopify.com/)

## Theme code principles

Before contributing to this project, please read the following theme code principles to better understand our fundamental approach to development. The expectation is that you follow these principles as you build for Shopify.

### Why these principles?

Browsers provide APIs to solve many problems: from [WebGL](https://en.wikipedia.org/wiki/WebGL) and [WASM](https://en.wikipedia.org/wiki/WebAssembly)-powered apps to static websites. The best APIs to use depends on the thing you’re building. Themes power ecommerce websites. In most cases, _Web-native_—making the most of the built-in features of browsers: HTTP, HTML, CSS, JavaScript, and the DOM—is a perfect fit for ecommerce websites. Ecommerce needs incredibly fast websites for mostly “logged out” traffic.

### Web-native in its purest form

_The most important principle._

Themes run on the [evergreen Web](https://www.w3.org/2001/tag/doc/evergreen-web/). We leverage the latest web browsers to their fullest, while maintaining support for the older ones through progressive enhancement—not polyfills.

We write bespoke Web-native code with no abstractions. Frameworks, libraries, and dependencies don’t belong in our Shopify themes.

We engage with the browser ecosystem on behalf of our merchants to make Web-native ecommerce the best it can be.

“Don’t repeat yourself” is an anti-pattern. We do our utmost best to do more with less, but we don’t build abstractions around repetition. Instead, we use linting and testing to enforce consistently-good and up-to-date Web-native code.

### Lean, fast, and reliable

_The principle requirement._

Code must be lean, fast, and reliable. Our targets include:

* Zero [Cumulative Layout Shift](https://web.dev/cls/)
* No DOM manipulation before user input
* No render-blocking JavaScript
* No [long tasks](https://developer.mozilla.org/en-US/docs/Web/API/Long_Tasks_API)

Functionality and design defaults to “no” until it meets this requirement. Code ships on quality.

We relentlessly and continuously optimize code within the constraint of being Web-native. If ever there is a feature that browsers have not made fast yet, we either don’t use it, or use it “as is” if it is fast enough. We trust that browsers will get faster over time.

Themes must be built with purpose. They shouldn’t support each and every feature in Shopify.

### JavaScript not required, fails gracefully

_NoJS is our baseline._

We extract every bit of speed and functionality out of HTTP, semantic HTML, and CSS before writing our first line of JavaScript.

JavaScript can only be used to progressively enhance features. JavaScript cannot be required to find or purchase products. And the little JavaScript that we use must always fail gracefully, such that every browser gets the most “enhanced” experience that it can within the capabilities that it has.

>:information_source: We do so not because we expect buyers to experience our storefronts with JavaScript disabled, but because it keeps us aligned with the other principles: writing fast, server-rendered, Web-native code.

### Server-rendered

_Our main constraint._

HTML must be rendered by Shopify servers using [Liquid](https://shopify.dev/api/liquid). Business logic and platform primitives such as translations and money formatting don’t belong on the client.

Server-rendered doesn’t imply “full page reload”. Async and on-demand rendering of parts of the page is OK, but we do it sparingly as a progressive enhancement.

### Functional, not pixel-perfect

_No buyer is left behind._

The Web doesn’t require each page to be rendered pixel-perfect by each browser engine. Using semantic markup, progressive enhancement, and clever design, we ensure that themes remain functional regardless of the browser.

And since legacy browsers are often the slowest, we don’t burden them with polyfills. We rely instead on the fail-open nature of the Web to provide them with a “minimal but functional” experience.

## Reporting a bug

When creating a new issue, please ensure the issue is clear and include additional details to help maintainers reproduce it:

* **Use a clear and descriptive title** for the issue to identify the problem.
* **Describe the exact steps which reproduce the problem** in as many details as possible.
* **Provide specific examples to demonstrate the steps.** Include links to files, or copy/pasteable snippets. If you're providing snippets in the issue, use Markdown code blocks.
* **Describe the behavior you observed** after following the steps and point out what exactly is the problem with that behavior.
* **Explain which behavior you expected to see** instead and why.
* **Include screenshots and animated GIFs** where possible.

## Reviewing

We (port80) view every single PR. The purpose of reviews is to create the best version we can for merchants, developers, and others who use this work.

:yellow_heart: Reviews are always respectful, acknowledging that everyone did the best possible job with the knowledge they had at the time.
:yellow_heart: Reviews discuss content, not the person who created it.
:yellow_heart: Reviews are constructive and start conversation around feedback.

### Self review

You should always review your own PR first.

For code changes, make sure that you:
- [ ] Confirm that the changes meet our [theme code principles](#theme-code-principles).
- [ ] Check new or updated Liquid docs to confirm that the code used is up to date and isn't deprecated.
- [ ] If there are any failing checks in your PR, troubleshoot them until they're all passing.
- [ ] Add @port80-rob as a reviewer

### Pull request template

When you open a pull request, you must fill out the template before we can review your PR. This template helps reviewers understand your changes and the purpose of your pull request.

### Suggested changes

We may ask for changes to be made before a PR can be merged, either using [suggested changes](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/incorporating-feedback-in-your-pull-request) or pull request comments. You can apply suggested changes directly through the UI. You can make any other changes in your source code, then commit them to your branch.

As you update your PR and apply changes, mark each conversation as [resolved](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/commenting-on-a-pull-request#resolving-conversations).
