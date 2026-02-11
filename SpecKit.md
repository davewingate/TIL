# GitHub Spec Kit

## Install Specify CLI
From [docs](https://github.com/github/spec-kit?tab=readme-ov-file#1-install-specify-cli):
```
brew install uv
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

## Specify Init
```
specify init --here --ai copilot
```

Files within `.github/prompts/` are available as AI agent commands.    
For example, in VS Code agent mode, type `/constitution` to see that the `/speckit.constitution` is available.

Files within `.specify/scripts/` are utilities referenced by the agent prompts.

Start using slash commands with your AI agent:
 1. /speckit.constitution - Establish project principles
 1. /speckit.specify - Create baseline specification
 1. /speckit.plan - Create implementation plan
 1. /speckit.tasks - Generate actionable tasks
 1. /speckit.implement - Execute implementation

## /speckit.specify

Starts a new git feature branch and creates a new `specs/nnn-foo-bar-baz/spec.md` file.

In the `spec.md` file you'll notice that your prompt was preserved in an `**Input**` section.  That prompt will have been used to generate one or more user stories in the spec.

Optional, but highly recommended, you should `/speckit.clarify` and then manually review the generated spec before moving forward.

## /speckit.plan

This step produces additional files within the `specs/nnn-foo-bar-baz/` directory.
 - `plan.md` - Whereas the `spec.md` should have focused on the "what" of the feature, the new `plan.md` begins to describe "how" to implement.
 - `research.md` - Document the high-level implementation choices being made during the plan phase.
 - `data-model.md` - Describe existing/new persist data model that will be used for the feature.  Additionally, describe the data model of API responses.

## Tutorials
[Up & Running with GitHub Spec Kit](https://www.youtube.com/playlist?list=PL4cUxeGkcC9h9RbDpG8ZModUzwy45tLjb)

## Documentation
[github / spec-kit](https://github.com/github/spec-kit)