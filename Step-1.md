# Clone Project

### Clone the Solution

The first step is to clone the project into a new folder.

```git clone https://github.com/gunjandatta/sprest-bs-starter sp-dashboard```

### Remove Repository Reference

We don't need a reference to the starter project, so we will remove the .git hidden directory.

```rm -r sp-dashboard/.git```

### Remove Unused Directories

We will not be using some of the code for this solution. Remove the following directories:

```rm -r sp-dashboard/dist```
```rm -r sp-dashboard/src/components```

### [[Next Step|Step 2]]