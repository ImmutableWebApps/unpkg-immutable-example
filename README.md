<h1>unpkg-immutable-example</h1>
<h2>Hosting an <a href="https://immutablewebapps.org">Immutable Web App</a> with <a href="https://www.npmjs.com/">npm</a>,
<a href="https://unpkg.com/#/">UNPKG</a>, and <a href="https://pages.github.com/">GitHub Pages</a></h2>
<p>Immutable Web Apps are composed of two concepts:</p>
<ul>
<li><b>Immutable Assets:</b> Static assets (javascript, CSS, images) that are hosted at a permanent, versioned,
    long-term browser cached location and that do not contain any environment-specific configuration.</li>
<br />
<li><b>Deployment Manifest:</b> An <code>index.html</code> that is unique to the environment and not cached by the
    browser. It contains environment-specific configuration, references to the versioned immutable assets, and meta
    data.</li>
</ul>
<p>Using a combination of npm, UNPKG, and Github Pages covers nearly all of these requirements!</p>
<ul>
<li><b><a href="https://www.npmjs.com/">npm</a>:</b> The software registry stores the the static assets in
    versioned, immutable packages.</li>
<br />
<li><b><a href="https://unpkg.com/#/">UNPKG</a>:</b> The CDN makes all assets of the package on npm addressable
    over https
    and globally available.</li>
<br />
<li><b><a href="https://pages.github.com/">GitHub Pages</a>:</b> This static hosting site supports easy
    configuration of DNS and Certificates, has great integration with GitHub (obviously), and has a short TTL for
    browser caching</li>
</ul>
<h2><i>This site is hosted using npm, UNPKG, and GitHub Pages!</i></h2>
<h3>Project Structure</h3>
<p>The git repository <a href="https://github.com/ImmutableWebApps/unpkg-immutable-example">unpkg-immutable-example</a>
is split into two critical branches:
<ul>
    <li><a href="https://github.com/ImmutableWebApps/unpkg-immutable-example/tree/default"><code>default</code></a>
    is where the Angular project is maintained. It was generated from Angular CLI and is generally maintained like
    any other static web application.</li>
    <br />
    <li><a href="https://github.com/ImmutableWebApps/unpkg-immutable-example/tree/master"><code>master</code></a> is
    configured to serve the GitHub Pages site. It only contains a single file <a href="https://github.com/ImmutableWebApps/unpkg-immutable-example/blob/master/404.html"><code>404.html</code></a>.
    This single file is served for every request made to the GitHub Pages site.</li>
</ul>
<h3>Project Lifecycle</h3>
<h4>Building</h4>
<p>Developing this web application is the same as any other. Features are built and tested locally, commits and
    pull requests advance the state of the codebase. When a stable version of the app is ready to be deployed, the
    assets are rendered to the <code>/dist</code> folder using <code>npm run build</code> and new version of the
    project is published to npm using <code>npm publish</code>. The assets become available on <a href="https://unpkg.com/@immutablewebapps/unpkg-immutable-example@0.0.1/">UNPKG</a>.</p>
<h4>Deploying</h4>
<p>With the new version of the assets available on UNPKG, we can trigger an <i>atomic</i> deployment by
    switching to the <code>master</code> branch and updating <code>404.html</code> with the new references to project
    assets via UNPKG as well as any related changes to environment variables. Once the commit is made, GitHub Pages
    deployment is triggered and the new version of the web application is available.</p>
<h4>Deploying to Another Environment</h4>
<p>Setup another <a href="https://github.com/ImmutableWebApps/unpkg-immutable-deployment">Github Pages repository</a>,
    add a <a href="https://github.com/ImmutableWebApps/unpkg-immutable-deployment/blob/master/404.html"><code>404.html</code></a>,
    and <a href="https://immutablewebapps.org/unpkg-immutable-deployment/">another deployment of the app</a> is
    created!</p>