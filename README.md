# Recipe APP API

A headless Umbraco CMS application that exposes recipe data through Umbraco Content Delivery API endpoints. This API serves as the backend for recipe-related applications, providing structured access to recipes, ingredients, and cooking instructions.

## Features

- **Headless CMS Architecture**: Built on Umbraco CMS with a focus on content delivery
- **API-First Approach**: All recipe data is exposed through RESTful API endpoints
- **Secure Access**: API endpoints are protected with API key authentication
- **Rich Content Model**: Supports structured recipe data including:
  - Recipe ingredients
  - Cooking instructions
  - Required utensils
  - Recipe metadata

## Technical Stack

- **.NET 9.0**: Core framework
- **Umbraco CMS 15.3.1**: Content management system
- **uSync 15.1.6**: Configuration and content synchronization
- **SQLite**: Development database (configurable for production)

## Content Types

### Recipe
The main content type that represents a cooking recipe. Each recipe includes:
- **Ingredients**: A collection of required ingredients, managed through a multi-node picker
- **Utensils**: Required cooking utensils for the recipe, managed through a multi-node picker
- **Cooking Instructions**: Step-by-step cooking instructions stored as multiple text strings
- **Example**: Spaghetti Bolognese, Birthday Cake, Beans on Toast

### Utensils
Represents cooking tools and equipment used in recipes:
- Managed through a dedicated utensil listing
- Can be associated with multiple recipes
- Examples include: Mixing Bowl, Whisk, Pan, Measuring Jug, Butter Knife

### Ingredients
Represents food items and cooking ingredients:
- Can be linked to multiple recipes
- Supports flexible ingredient management
- Examples include: Tagliatelle, Bolognese Sauce, Cake Mix

## Setup

1. Clone the repository
2. Ensure you have .NET 9.0 SDK installed
3. Configure the database connection string in `appsettings.json`
4. Set up your API key in configuration
5. Run the application:
   ```bash
   dotnet run
   ```

## API Security

The API is secured using API key authentication. All requests to `/umbraco/delivery` endpoints must include the `X-Api-Key` header with the configured API key.

Example:
```http
GET /umbraco/delivery/api/v1/content
X-Api-Key: your-api-key-here
```

## Development

- Development settings are configured in `appsettings.Development.json`
- Uses SQLite database by default in development
- Debug mode is enabled in development environment
- Supports hot reload for development

## Configuration

Key configuration files:
- `appsettings.json`: Main application configuration
- `appsettings.Development.json`: Development-specific settings
- `uSync/`: Content type and data type configurations

## Content Synchronization

The project uses uSync for content and configuration synchronization. All content types, data types, and media types are version controlled and can be synchronized across environments.
