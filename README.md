# Setup Subversion Action

A GitHub Action to install Apache Subversion (svn) on Ubuntu, macOS, and Windows runners.

## Usage

Add this step to your workflow:

```yaml
- uses: ampscm/setup-subversion@v1
```

### Complete Workflow Example

```yaml
name: SVN Checkout Example

on: [push, pull_request]

jobs:
  checkout:
    runs-on: ubuntu-latest
    
    steps:
      - name: Setup Subversion
        uses: ampscm/setup-subversion@v1
        
      - name: Checkout SVN repository
        run: |
          svn checkout https://svn.example.com/repo/trunk
          
      - name: Show SVN info
        run: svn info
```

### Multi-Platform Example

```yaml
name: Multi-Platform SVN

on: [push]

jobs:
  test:
    strategy:
      matrix:
        os: [ubuntu-latest, macos-latest, windows-latest]
    
    runs-on: ${{ matrix.os }}
    
    steps:
      - name: Setup Subversion
        uses: ampscm/setup-subversion@v1
        
      - name: Verify SVN installation
        run: svn --version
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `svn-version` | Version of Subversion to install | No | Latest available |

## Outputs

| Output | Description |
|--------|-------------|
| `svn-version` | The installed version of Subversion |

### Using Outputs

```yaml
- name: Setup Subversion
  id: svn
  uses: ampscm/setup-subversion@v1
  
- name: Display version
  run: echo "Installed SVN version ${{ steps.svn.outputs.svn-version }}"
```

## Supported Platforms

- **Ubuntu/Debian Linux**: Installs via `apt-get`
- **macOS**: Installs via Homebrew
- **Windows**: Installs via Chocolatey

## License

This action is released under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
