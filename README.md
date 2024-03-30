`typescript-ex`
---------------

Is a "hello world" application written on TypeScript, it shows the [Shipwright's][shipwright] logo (`./assets/images/shipwright-logo.png`) in a simple page.

# Building and Running

To build the application run the following commands:

```bash
npm install
npm run build
```

Now you are ready to run the application from your workstation with:


```bash
npm run start
```

Test the application endpoint with `curl`:

```bash
curl 127.0.0.1:8080
```

# CI

## OpenShift Pipelines (Tekton)

The resource to run continuous-integration jobs are documented on the [`ci/tekton` directory](./ci/tekton/).


[shipwright]: https://github.com/shipwright-io
[buildpacksPack]: https://buildpacks.io/docs/tools/pack/