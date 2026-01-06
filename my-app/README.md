Rendering Strategy for DailyEdge

DailyEdge initially used static generation for its homepage to achieve fast load times, but this caused the “Breaking News” section to display outdated headlines. Switching entirely to server-side rendering fixed the freshness issue but resulted in slower performance and higher hosting costs. To balance speed, freshness, scalability, and cost, DailyEdge adopted a hybrid rendering strategy using the Next.js App Router.

The About page uses Static Site Generation with dynamic = 'force-static' because its content rarely changes. Pre-rendering at build time ensures fast CDN delivery, improved SEO, minimal server usage, and excellent scalability.

The Dashboard page uses Server-Side Rendering with dynamic = 'force-dynamic' to handle authenticated, user-specific data. Rendering on every request ensures accurate, secure, and up-to-date content, which is essential for personalized user experiences.

The Breaking News page uses Incremental Static Regeneration with revalidate = 60. This allows headlines to refresh every minute in the background while serving cached content instantly, keeping news timely without sacrificing performance or increasing server load.

Overall, this hybrid approach enables DailyEdge to deliver fast and fresh content while controlling infrastructure costs and maintaining a smooth user experience.


## Environment Segregation & Secure Secret Management

### Overview
This project follows strict environment segregation to ensure safe, reliable, and predictable deployments. Separate configurations are maintained for development, staging, and production to prevent accidental data corruption, secret leakage, and downtime.

---

### Supported Environments

| Environment | Purpose |
|------------|---------|
| Development | Local development and testing |
| Staging | Pre-production validation |
| Production | Live system for end users |

Each environment operates in isolation and uses its own configuration and infrastructure.

---

### Environment Configuration Files

The project uses environment-specific configuration files: