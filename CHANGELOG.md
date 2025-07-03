# CHANGELOG

## v2.0.0 - Cloudflare D1 Support

### 🚀 Major Features

- **Cloudflare D1 Support**: Full support for Cloudflare D1 database
- **Edge Computing Ready**: Optimized for Cloudflare Workers and edge computing
- **Multi-Platform**: Supports both Node.js (SQLite) and Cloudflare Workers (D1)
- **Runtime Detection**: Automatically detects runtime environment and selects appropriate database driver

### 🔧 Technical Changes

- **Async API**: All data provider methods are now asynchronous
- **Database Adapter**: Added `DatabaseAdapter` class to unify database operations
- **Type Safety**: Enhanced TypeScript type definitions
- **Parameter Binding**: Uses parameterized queries to prevent SQL injection

### 📁 New Files

- `src/types.ts` - Cloudflare D1 and common type definitions
- `src/database.ts` - Database adapter and runtime detection
- `src/worker.ts` - Cloudflare Workers example implementation
- `wrangler.toml` - Cloudflare Workers configuration
- `migrations/001_initial.sql` - Example database schema
- `examples/usage.ts` - Usage examples
- `CLOUDFLARE.md` - Cloudflare D1 support documentation
- `DEPLOYMENT.md` - Deployment guide

### 🔄 Breaking Changes

- **Async Methods**: All data provider methods now return Promises
- **Constructor**: `dataProvider()` now accepts `string | D1Database` parameter
- **Dependencies**: Added Cloudflare Workers related dependencies

### 📦 Dependencies

#### Added
- `@cloudflare/workers-types` - Cloudflare Workers type definitions
- `wrangler` - Cloudflare Workers CLI tool

#### Updated
- Enhanced TypeScript configuration for multi-platform support

### 🏗️ Build System

- **Scripts**: Added `dev:worker` and `deploy:worker` scripts
- **TypeScript**: Updated configuration to support Cloudflare Workers and Node.js
- **Build**: Maintains compatibility with existing build system

### 📚 Documentation

- **README**: Updated to include Cloudflare D1 support information
- **Examples**: Provides complete usage examples for both SQLite and D1
- **Deployment**: Detailed deployment guide and best practices
- **API Reference**: Updated API documentation

### 🔒 Security

- **Parameter Binding**: All SQL queries now use parameterized queries
- **Input Validation**: Enhanced input validation and error handling
- **Type Safety**: Stricter TypeScript type checking

### 🚀 Performance

- **Edge Optimization**: Optimized for edge computing environments
- **Connection Pooling**: Automatic connection management for D1
- **Minimal Bundle**: Reduced unnecessary dependencies

### 🔧 Migration Guide

#### From v1.x to v2.0

1. **Update method calls** to use async/await:
   ```typescript
   // Before (v1.x)
   const result = provider.getList({ resource: 'posts' });
   
   // After (v2.0)
   const result = await provider.getList({ resource: 'posts' });
   ```

2. **For Cloudflare Workers**, pass D1Database instance:
   ```typescript
   // Cloudflare Workers
   const provider = dataProvider(env.DB);
   
   // Node.js (unchanged)
   const provider = dataProvider('./database.db');
   ```

3. **Update package.json** scripts for Cloudflare Workers:
   ```json
   {
     "scripts": {
       "dev:worker": "wrangler dev",
       "deploy:worker": "wrangler deploy"
     }
   }
   ```

### 🎯 Roadmap

- [ ] Enhanced filtering and sorting for D1
- [ ] Real-time subscriptions with Cloudflare Durable Objects
- [ ] Performance optimizations for large datasets
- [ ] Advanced caching strategies

### 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### 📄 License

MIT License - see [LICENSE.md](LICENSE.md) for details.
