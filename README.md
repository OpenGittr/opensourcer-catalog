# Opensourcer Catalog

A curated collection of self-hosted open source software configurations for easy deployment.

## Structure

Each software has its own folder containing:

```
<software>/
├── app.json              # Software metadata and configuration
├── docker-compose.yaml   # Docker Compose deployment file
└── [optional configs]    # Additional configuration files
```

### app.json Schema

```json
{
  "name": "Software Name",
  "description": "Brief description",
  "icon": "https://example.com/icon.png",
  "website": "https://example.com",
  "category": "category-slug",
  "tags": ["tag1", "tag2"],
  "inputs": {
    "domain": {
      "label": "Domain name",
      "placeholder": "example.com",
      "required": true,
      "type": "text",
      "description": "Your domain"
    }
  },
  "services": {
    "app": {
      "exposed": true,
      "stateless": false
    },
    "db": {
      "internal": true,
      "managed_option": "postgres"
    }
  }
}
```

## Categories

Categories are defined in `_categories.json`:

- **analytics** - Web analytics and tracking
- **automation** - Workflow automation tools
- **cms** - Content management systems
- **communication** - Chat and messaging
- **devtools** - Developer tools
- **media** - Media servers and streaming
- **monitoring** - Uptime and performance monitoring
- **productivity** - Office and collaboration tools
- **security** - Password managers and security tools

## Contributing

We welcome contributions! To add new software:

1. Fork this repository
2. Create a new folder with the software slug (lowercase, hyphenated)
3. Add `app.json` with metadata
4. Add `docker-compose.yaml` for local deployment
5. Test the deployment locally
6. Submit a pull request

### Guidelines

- Use official Docker images when available
- Include health checks where possible
- Use environment variables for configuration
- Document any required setup steps
- Keep compose files simple and focused

## Usage

This catalog is used by the [Opensourcer CLI](https://github.com/opengittr/opensourcer-cli):

```bash
# Install CLI
go install github.com/opengittr/opensourcer-cli@latest

# Update catalog
opensourcer update

# List available software
opensourcer catalog

# Deploy software
opensourcer deploy <software>
```

## License

MIT
