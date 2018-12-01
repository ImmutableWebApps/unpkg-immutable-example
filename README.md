<h1>unpkg-immutable-example</h1>
<h2>Hosting an <a href="https://immutablewebapps.org">Immutable Web App</a> with <a href="https://www.npmjs.com/">npm</a>,
    <a href="https://unpkg.com/#/">UNPKG</a>, and <a href="https://pages.github.com/">GitHub Pages</a></h2>
<p>Immutable Web Apps are composed of two concepts:</p>
<ul>
    <li><b>Immutable Assets:</b> Static assets (javascript, CSS, images) that do not contain any
        environment-specific
        configuration and are hosted at a permanent, versioned,
        long-term browser cached location.</li>
    <br />
    <li><b>Deployment Manifest:</b> An <code>index.html</code> that is unique to the environment and not cached by
        the
        browser. It contains environment-specific configuration, references to the versioned immutable assets, and
        meta
        data.</li>
</ul>
<p>Using a combination of npm, UNPKG, and Github Pages covers nearly all of these requirements!</p>
<ul>
    <li><b><a href="https://www.npmjs.com/">npm</a>:</b> The software registry stores the the static assets in
        versioned, immutable packages. <i>Perfect for managing the immutable assets!</i></li>
    <br />
    <li><b><a href="https://unpkg.com/#/">UNPKG</a>:</b> The CDN makes all assets of the packages on npm
        addressable
        over https
        and globally available. <i>Perfect for delivering the immutable assets!</i></li>
    <br />
    <li><b><a href="https://pages.github.com/">GitHub Pages</a>:</b> This static hosting site supports easy
        configuration of DNS and HTTPS, has great integration with GitHub (obviously), and has a short TTL for
        browser caching. <i>Perfect for serving the deployment manifest!</i></li>
</ul>
<h2><i>This Immutable Web App is hosted using npm, UNPKG, and GitHub Pages!</i></h2>
<h3>Project Structure</h3>
<p>The git repository <a href="https://github.com/ImmutableWebApps/unpkg-immutable-example">unpkg-immutable-example</a>
    is split into two critical branches:</p>
<ul>
    <li><a href="https://github.com/ImmutableWebApps/unpkg-immutable-example/tree/default"><code>default</code></a>
        is where the Angular project is maintained. It was generated from Angular CLI and is maintained like
        any other static web application.</li>
    <br />
    <li><a href="https://github.com/ImmutableWebApps/unpkg-immutable-example/tree/master"><code>master</code></a>
        is
        configured to serve the GitHub Pages site. It only contains a single file <a href="https://github.com/ImmutableWebApps/unpkg-immutable-example/blob/master/404.html"><code>404.html</code></a>.
        This single file is <a href="https://help.github.com/articles/creating-a-custom-404-page-for-your-github-pages-site/">served
            for every request</a> made to the GitHub Pages site.</li>
</ul>
<h3>Project Lifecycle</h3>
<h4>Building</h4>
<p>Developing this web application is the same as any other single-page app node project. Features are built
    and tested locally, commits and
    pull requests advance the state of the codebase. When a stable version of the app is ready to be deployed,
    the
    assets are rendered to the <code>/dist</code> folder using <code>npm run build</code> and new version of
    the
    project is published to npm using <code>npm publish</code>. The assets become available on <a href="https://unpkg.com/@immutablewebapps/unpkg-immutable-example/">UNPKG</a>.</p>
<h4>Deploying</h4>
<p>With the new version of the assets available on UNPKG, an <i>atomic</i> deployment can be triggered by
    switching to the <code>master</code> branch and updating <code>404.html</code> with the references to the
    new project
    assets and any changes to environment variables. Once the commit is is pushed to the GitHub repository,
    GitHub Pages
    deployment is triggered and the new version of the web application is available.</p>
<h2><i>Deployments!</i></h2>
<p>With our Immutable Web App hosted by npm/UNPKG and without any environment-specific configuration,
    deployments
    are cheap and reliable! Let's deploy <code>index.html</code> to wherever it is easiest to setup DNS and
    HTTPS!</p>
<h3>Deploy to another Github Pages repository</h3>
<p><i>and let's change the version!</i></p>
<ul>
    <li>Fork <a href="https://github.com/ImmutableWebApps/unpkg-immutable-deployment">unpkg-immutable-deployment</a></li>
    <li><a href="https://help.github.com/articles/configuring-a-publishing-source-for-github-pages/">Configure
            the
            repo as a publishing source for Github Pages</a></li>
    <li>Modify the <code>404.html</code> to point to a different version</li>
    <li><a href="https://immutablewebapps.org/unpkg-immutable-deployment"><b><i>Deployed!</i></b></a></li>
</ul>
<h3>Deploy to Netlify</h3>
<p><i>and let's change some environment variables!</i></p>
<ul>
    <li><code>git clone
        https://github.com/ImmutableWebApps/unpkg-immutable-deployment</code></li>
    <li><code>cd unpkg-immutable-deployment</code></li>
    <li><a href="https://app.netlify.com/">Create a Netlify account</a></li>
    <li>Run <code>npm i -g netlify-cli</code></li>
    <li>Run <code>netlify login</code></li>
    <li>Run <code>netlify deploy</code></li>
    <li><a href="https://immutablewebapps.netlify.com"><b><i>Deployed!</i></b></a></li>
</ul>
<h3>Deploy Locally</h3>
<p><i>and configure it however you want! Try loading up some <a href="https://github.com/ImmutableWebApps/unpkg-immutable-example/releases">older
            versions!</a></i></p>
<ul>
    <li><code>git clone
        https://github.com/ImmutableWebApps/unpkg-immutable-deployment.git</code></li>
    <li><code>cd unpkg-immutable-deployment</code></li>
    <li><code>npm i -g ecstatic</code></li>
    <li><code>ecstatic</code> (<a href="https://www.npmjs.com/package/ecstatic">ecstatic</a> is a simple static
        file server)</li>
    <li><a href="http://0.0.0.0:8000"><b><i>Deployed!</i></b></a></li>
</ul>