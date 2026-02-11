# Development

This company is mainly an IT startup company with a main focus on Computer Networking. As such, only a few essential software projects are going to be made compared to a Software-as-a-Service company or larger companies.

We work mainly on a Wordpress website that acts as landing page for the company. We also occasionally work on internal tooling to support internal operations.

## Contributing changes

The first step is to set up a copy of the Git repository of the project you want to contribute to. We follow a "feature-branch, and PR" model for contributions.

1. On GitHub, "Fork" the project repository you wish to contribute to, to your own user account using the "Fork" button in the relevant repository.

2. Clone your fork to your local machine and enter the directory:
```bash
git clone git@github.com:yourusername/projectname.git
cd projectname/
```

3. Add the "upstream" remote, which allows you to pull down changes from the main project easily:
```bash
git remote add upstream git@github.com:ELEISS-OPC/projectname.git
```

4. When contributing code, ensure that you have read the [guidelines](/documentation/development/artifacts/style-guides/#contributing-code) before making commits and changes to the code. See the relevant documentation on how to run a development server for the 
