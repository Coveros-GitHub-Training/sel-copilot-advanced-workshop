# Best Practices for Repository Custom Instructions

## Overview

GitHub Copilot supports custom instructions at the repository level to guide AI-assisted development and ensure code consistency across your project. Understanding how to effectively use both repository-wide and path-specific instructions is essential for maximizing Copilot's effectiveness.

This guide provides evidence-based best practices with practical, real-world examples focused specifically on **repository custom instructions** (not user-level personal instructions).

## Types of Repository Custom Instructions

GitHub Copilot supports two types of custom instructions within a repository:

### 1. **Repository-Wide Instructions** (`.github/copilot-instructions.md`)
- **Location**: Single file at `.github/copilot-instructions.md`
- **Scope**: Applies to **all files** in the repository
- **Purpose**: Define universal standards, tech stack, and patterns for the entire project
- **Best For**: Broad, consistent standards that affect the entire codebase

### 2. **Path-Specific Instructions** (`.github/instructions/*.instructions.md`)
- **Location**: Multiple files in `.github/instructions/` directory
- **Scope**: Applies only to files matching specified `applyTo` patterns
- **Purpose**: Provide targeted guidance for specific parts of the codebase
- **Best For**: Different conventions for frontend/backend, security-sensitive areas, or legacy code

## How They Work Together

**Research Finding**: Both instruction types work together through **context merging**. When editing a file:
1. Repository-wide instructions (`.github/copilot-instructions.md`) are always included
2. Any matching path-specific instructions are also included
3. Copilot merges all relevant instructions to inform its suggestions

**Important**: There's no strict priority hierarchy - Copilot uses all matching instructions as context. This means instructions should complement each other, not conflict.

## When to Use Each Type

| Scenario | Repository-Wide<br>(`copilot-instructions.md`) | Path-Specific<br>(`.instructions.md`) |
|----------|---------------------------------------------|----------------------------------|
| Technology stack and frameworks | ✅ | ❌ |
| Universal coding standards | ✅ | ❌ |
| Project architecture overview | ✅ | ❌ |
| Frontend-specific React patterns | ❌ | ✅ |
| Backend API conventions | ❌ | ✅ |
| Security-sensitive file handling | ❌ | ✅ |
| Test file requirements | ❌ | ✅ |
| Legacy code modernization hints | ❌ | ✅ |
| Monorepo with multiple sub-projects | ❌ | ✅ |

---

# Part 1: Repository-Wide Instructions (`.github/copilot-instructions.md`)

## Why Repository-Wide Instructions Matter

Repository-wide custom instructions are the **foundation** of effective AI-assisted development. Research shows that teams using well-crafted repository instructions report:

- **50%+ increase** in coding productivity
- **3-4x faster** feature delivery
- **60% reduction** in code review cycles
- **Improved onboarding** for new team members

These instructions serve critical purposes:
- **Team Consistency**: All contributors receive the same project-specific guidance
- **Code Quality**: Enforce architectural patterns and coding standards automatically
- **Living Documentation**: Version-controlled documentation of project decisions
- **Onboarding**: Help new developers understand conventions quickly
- **Standards Enforcement**: Prevent introducing outdated or incompatible patterns

## Best Practices for Repository-Wide Instructions

### 1. Start with a Clear Project Overview

Help Copilot understand what the project does and who it's for.

**Evidence-Based Recommendation**: Research shows that context and clarity are the most critical factors in instruction effectiveness.

**Real-World Examples:**

**Example 1: E-Commerce Platform**
```markdown
# Project Overview
This is an e-commerce platform for online retail operations. Built with microservices architecture using REST APIs. The system prioritizes scalability, data consistency, and payment security.

## Target Users
- Customers browsing and purchasing products
- Merchants managing inventory and orders
- Administrators monitoring system health

## Core Functionality
- Product catalog with search and filtering
- Shopping cart and checkout process
- Payment processing integration
- Order management and fulfillment tracking
- Inventory management system
```

**Example 2: DevOps Automation Tool**
```markdown
# Project Overview
This is a cloud infrastructure automation tool for managing multi-cloud deployments. Uses Infrastructure-as-Code principles with Terraform and Ansible. Focuses on idempotency, security, and cost optimization.

## Target Users
- DevOps engineers deploying infrastructure
- SREs monitoring system reliability
- Security teams auditing configurations

## Core Functionality
- Infrastructure provisioning and configuration
- CI/CD pipeline automation
- Security compliance scanning
- Cost optimization recommendations
- Multi-cloud resource management
```

**Example 3: Data Analytics Platform**
```markdown
# Project Overview
This is a data analytics platform for processing and visualizing large datasets. Built with Python, Apache Spark, and PostgreSQL. Emphasizes data quality, performance, and reproducibility.

## Target Users
- Data scientists building models
- Business analysts creating reports
- Data engineers maintaining pipelines

## Core Functionality
- ETL data pipelines
- Real-time data processing
- Statistical analysis and ML models
- Interactive dashboards and visualizations
- Data governance and lineage tracking
```

**Why This Works**: Copilot can make context-aware suggestions that fit your application's domain, purpose, and technical requirements.

### 2. Define the Technology Stack Explicitly

Specify exact versions and choices to avoid incompatible suggestions.

**Evidence-Based Recommendation**: Specific technology declarations prevent Copilot from suggesting outdated patterns or incompatible libraries found in the project's history.

**Real-World Examples:**

**Example 1: Python Microservices**
```markdown
## Technology Stack
- **Language**: Python 3.11+ with type hints
- **Framework**: FastAPI for REST APIs (not Flask)
- **Database**: PostgreSQL 15+ with SQLAlchemy ORM
- **Message Queue**: RabbitMQ for async communication
- **Authentication**: OAuth 2.0 with JWT tokens
- **Testing**: pytest with pytest-asyncio
- **Code Quality**: Black for formatting, Flake8 for linting, MyPy for type checking
- **Containerization**: Docker with multi-stage builds
```

**Example 2: Java Enterprise Application**
```markdown
## Technology Stack
- **Language**: Java 17 LTS (use records, sealed classes, pattern matching)
- **Framework**: Spring Boot 3.x with Spring Security
- **Database**: Oracle 19c with JPA/Hibernate
- **Build Tool**: Maven 3.9+ (not Gradle)
- **Testing**: JUnit 5 + Mockito for unit tests, TestContainers for integration tests
- **Code Quality**: Checkstyle with Google Java conventions
- **Logging**: SLF4J with Logback
- **API Documentation**: OpenAPI 3.0 with SpringDoc
```

**Example 3: Infrastructure-as-Code**
```markdown
## Technology Stack
- **IaC Tool**: Terraform 1.5+ (HCL syntax, not JSON)
- **Cloud Provider**: AWS (use latest provider version)
- **Configuration**: Ansible for post-provisioning configuration
- **CI/CD**: GitHub Actions for automated deployments
- **Secret Management**: AWS Secrets Manager (not environment variables in code)
- **Testing**: Terratest for infrastructure validation
- **State Management**: S3 backend with DynamoDB state locking
- **Cost Optimization**: Infracost for cost analysis
```

**Example 4: .NET Microservices**
```markdown
## Technology Stack
- **Language**: C# 12 with .NET 8
- **Framework**: ASP.NET Core for REST APIs, gRPC for inter-service communication
- **Database**: SQL Server 2022 with Entity Framework Core
- **Message Broker**: Azure Service Bus
- **Testing**: xUnit with FluentAssertions
- **Code Quality**: StyleCop analyzers, SonarQube
- **Logging**: Serilog with structured logging
- **Package Management**: NuGet with central package management
```

**Why This Works**: Specific technology declarations prevent Copilot from suggesting deprecated patterns, incompatible libraries, or outdated approaches from the project's history.

### 3. Document Architecture and Code Organization

Define where code lives and how components should be structured.

**Evidence-Based Recommendation**: Clear architectural guidance helps Copilot place new code in the right locations and follow established patterns.

**Real-World Examples:**

**Example 1: Microservices Architecture**
```markdown
## Project Structure

services/
├── user-service/        # User authentication and profile management
│   ├── api/            # REST API endpoints
│   ├── models/         # Data models and schemas
│   ├── services/       # Business logic
│   └── tests/          # Unit and integration tests
├── order-service/       # Order processing and management
├── payment-service/     # Payment processing
└── shared/             # Shared utilities and types

## Architecture Patterns
- Each service is independently deployable
- Services communicate via REST APIs or message queues
- Use repository pattern for data access
- Implement circuit breaker pattern for resilience
- Apply CQRS for read-heavy operations
- Use API Gateway for external access

## Service Guidelines
- Each service has its own database (database per service)
- Services expose health check endpoints
- Use correlation IDs for distributed tracing
- Implement idempotent operations
- Version all APIs (v1, v2, etc.)
```

**Example 2: Monorepo Structure**
```markdown
## Project Structure

packages/
├── api/                # Backend REST API
│   ├── controllers/   # Request handlers
│   ├── middleware/    # Express middleware
│   ├── models/        # Database models
│   └── routes/        # API routes
├── cli/               # Command-line tools
├── shared/            # Shared code between packages
│   ├── types/        # TypeScript type definitions
│   ├── utils/        # Utility functions
│   └── constants/    # Shared constants
├── worker/            # Background job processors
└── web/               # Web application

## Architecture Patterns
- Workspaces managed by npm/yarn/pnpm workspaces
- Shared dependencies defined at root
- Each package can be built independently
- Use Lerna or Nx for monorepo management
- Shared code must be backward compatible
```

**Example 3: Layered Architecture**
```markdown
## Project Structure

src/
├── controllers/       # Presentation layer - handles HTTP requests
├── services/          # Business logic layer
├── repositories/      # Data access layer
├── models/            # Domain models and entities
├── dto/               # Data Transfer Objects
├── middleware/        # Cross-cutting concerns
├── config/            # Configuration files
└── utils/             # Helper functions

## Architecture Patterns
- Controllers: Thin, delegate to services, handle HTTP concerns only
- Services: Business logic, no direct database access
- Repositories: Data access abstraction, queries and persistence
- Models: Domain entities, business rules validation
- Use dependency injection throughout
- Follow SOLID principles
- Apply separation of concerns

## Guidelines
- Controllers don't call repositories directly
- Services don't handle HTTP responses
- Repositories return domain models, not raw database objects
- Use DTOs for API contracts
```

**Why This Works**: Clear structural guidance helps Copilot place new code in the correct locations and follow established architectural patterns across any language or framework.

### 4. Specify Code Style and Conventions

Define the specific formatting, naming, and code organization standards for your project.

**Evidence-Based Recommendation**: Specific, actionable guidance works far better than vague directives like "write clean code."

**Real-World Examples:**

**Example 1: Python Project Standards**
```markdown
## Code Style Standards
- **Naming Conventions**:
  - snake_case for functions, variables, and modules
  - PascalCase for classes
  - SCREAMING_SNAKE_CASE for constants
  - Prefix private members with single underscore

- **File Organization**:
  - One class per file for large classes
  - Group related functions in modules
  - Import order: standard library → third-party → local
  - Use absolute imports over relative

- **Type Hints**:
  - Use type hints for all function signatures
  - Use Optional for nullable values
  - Define TypedDict for dictionary structures
  - Run MyPy in strict mode

- **Functions**:
  - Max function length: 50 lines
  - Use docstrings (Google or NumPy style)
  - Avoid deep nesting (max 3 levels)
  - Prefer early returns

- **Comments**:
  - Docstrings for all public functions and classes
  - Inline comments to explain complex logic
  - Document exceptions and edge cases
```

**Example 2: Java/C# Enterprise Standards**
```markdown
## Code Style Standards
- **Naming Conventions**:
  - camelCase for methods and variables
  - PascalCase for classes and interfaces
  - UPPER_SNAKE_CASE for static final constants
  - Prefix interfaces with 'I' (C# only)

- **File Organization**:
  - One public class per file
  - Organize members: fields → constructors → methods
  - Group by access modifier: public → protected → private

- **Documentation**:
  - XML documentation comments for public APIs (C#)
  - Javadoc for all public methods (Java)
  - Document parameters, return values, and exceptions
  - Include usage examples for complex APIs

- **Methods**:
  - Max method length: 30 lines
  - Extract complex conditions into named methods
  - Use async/await for I/O operations (C#)
  - Handle exceptions at appropriate levels

- **Error Handling**:
  - Use specific exception types
  - Never catch System.Exception (C#) or Exception (Java)
  - Always include context in exception messages
  - Log exceptions with stack traces
```

**Example 3: General Best Practices (Language-Agnostic)**
```markdown
## Code Style Standards
- **Naming Conventions**:
  - Use descriptive names that reveal intent
  - Avoid abbreviations except well-known ones (HTTP, API, URL)
  - Boolean names should read like questions: canDelete, hasPermission
  - Collections should be plural: users, orders, items

- **Function Design**:
  - Functions should do one thing well (Single Responsibility)
  - Max parameters: 3 (use objects for more)
  - Avoid side effects in functions
  - Pure functions when possible
  - Max cyclomatic complexity: 10

- **Code Organization**:
  - Group related code together
  - Separate concerns (presentation, business logic, data access)
  - Use consistent file naming across the project
  - Keep files under 400 lines

- **Error Handling**:
  - Fail fast - validate inputs early
  - Use specific error types
  - Provide actionable error messages
  - Log errors with context
  - Don't swallow exceptions

- **Comments and Documentation**:
  - Code should be self-documenting
  - Comment "why" not "what"
  - Update comments when code changes
  - Remove commented-out code
  - Document assumptions and constraints
```

**Why This Works**: Language-appropriate standards ensure Copilot generates code that matches your team's conventions, regardless of the technology stack.

### 5. Include Security Requirements

Define security standards that should be followed in all generated code.

**Evidence-Based Recommendation**: Security vulnerabilities are costly. Having Copilot follow security patterns by default significantly reduces risk.

**Real-World Examples:**

**Example 1: API Security**
```markdown
## Security Requirements
- **Authentication**: Use OAuth 2.0 with JWT tokens, rotate refresh tokens
- **Authorization**: Implement role-based access control (RBAC)
- **Input Validation**: Validate all inputs against strict schemas (JSON Schema, Joi, Pydantic)
- **SQL Injection**: Use parameterized queries or ORM, never string concatenation
- **API Rate Limiting**: Implement rate limiting (e.g., 100 requests/minute per user)
- **CORS**: Configure CORS restrictively, whitelist specific origins only
- **Secrets Management**: Use environment variables or secret managers (AWS Secrets Manager, Azure Key Vault)
- **Logging**: Log security events (auth failures, privilege escalations) but never log sensitive data

## Example (Python with SQLAlchemy)
# Good: Parameterized query
user = session.query(User).filter(User.id == user_id).first()

# Bad: String concatenation (SQL injection risk)
# query = f"SELECT * FROM users WHERE id = '{user_id}'"
```

**Example 2: Infrastructure Security**
```markdown
## Security Requirements
- **Network**: Use private subnets, security groups with least privilege
- **Encryption**: Enable encryption at rest and in transit (TLS 1.3)
- **IAM**: Apply principle of least privilege, use service accounts not root
- **Secrets**: Never hard-code credentials, use secret rotation
- **Compliance**: Enable audit logging (CloudTrail, Azure Monitor)
- **Container Security**: Scan images for vulnerabilities, use minimal base images
- **Access Control**: Use SSH keys not passwords, enable MFA for admin access

## Example (Terraform)
# Good: Reference secret from secret manager
db_password = data.aws_secretsmanager_secret_version.db_password.secret_string

# Bad: Hard-coded password
# db_password = "MyP@ssw0rd123"
```

**Example 3: Web Application Security**
```markdown
## Security Requirements
- **XSS Prevention**: Sanitize all user input, use Content Security Policy (CSP)
- **CSRF Protection**: Use anti-CSRF tokens for state-changing operations
- **Session Security**: Set HttpOnly and Secure flags on cookies
- **Password Storage**: Use bcrypt/Argon2 with work factor >= 12
- **File Uploads**: Validate MIME types, scan for malware, restrict file sizes
- **Dependency Security**: Regularly update dependencies, scan with tools (npm audit, Snyk)
- **Error Handling**: Return generic error messages to users, log detailed errors server-side
- **Headers**: Set security headers (X-Frame-Options, X-Content-Type-Options, HSTS)

## Example (Express.js middleware)
// Good: Input validation and sanitization
app.post('/api/users', 
  body('email').isEmail().normalizeEmail(),
  body('name').trim().escape(),
  validateRequest,
  createUserHandler
);
```

**Critical Impact**: Security patterns built into generated code from the start prevent vulnerabilities across any technology stack, reducing the need for extensive security audits later.

### 6. Document Deprecated Patterns

**Evidence-Based Practice**: Explicitly list patterns to avoid prevents Copilot from suggesting outdated code from project history.

**Real-World Example:**
```markdown
## Deprecated Patterns (Do Not Use)
- ❌ Class components - use functional components with hooks
- ❌ Pages Router - we use App Router only
- ❌ `any` type - use explicit types or `unknown`
- ❌ CSS-in-JS - use Tailwind classes
- ❌ `!important` in CSS - fix specificity instead
- ❌ Global state - use React Context or props

## Why These Are Deprecated
- Class components: Maintenance burden, hooks provide better patterns
- Pages Router: App Router provides better performance and features
- `any` type: Defeats purpose of TypeScript, causes runtime errors
```

**Impact**: Prevents Copilot from mimicking old patterns still present in the codebase.

### 7. Provide Code Examples

**Research Finding**: Concrete examples significantly improve Copilot's ability to generate consistent code.

**Real-World Examples:**

**Example 1: API Endpoint Pattern (Python/FastAPI)**
```markdown
## API Endpoint Pattern

Follow this pattern for all REST API endpoints:

from fastapi import APIRouter, Depends, HTTPException, status
from pydantic import BaseModel
from typing import List
from services.auth import get_current_user
from services.orders import OrderService

router = APIRouter(prefix="/api/v1/orders", tags=["orders"])

class OrderResponse(BaseModel):
    id: int
    user_id: int
    total: float
    status: str

@router.get("/", response_model=List[OrderResponse])
async def get_orders(
    current_user: User = Depends(get_current_user),
    order_service: OrderService = Depends()
) -> List[OrderResponse]:
    """
    Get all orders for the current user.
    
    Returns:
        List of orders with details
        
    Raises:
        HTTPException: If user is unauthorized or service fails
    """
    try:
        orders = await order_service.get_user_orders(current_user.id)
        return [OrderResponse(**order.dict()) for order in orders]
    except ServiceException as e:
        raise HTTPException(
            status_code=status.HTTP_500_INTERNAL_SERVER_ERROR,
            detail=f"Failed to fetch orders: {str(e)}"
        )

# Always:
# - Use dependency injection
# - Define Pydantic models for request/response
# - Include proper error handling
# - Add docstrings
# - Use type hints
```

**Example 2: Service Layer Pattern (Java/Spring)**
```markdown
## Service Layer Pattern

Follow this pattern for all business logic services:

@Service
@Transactional
public class OrderService {
    
    private final OrderRepository orderRepository;
    private final PaymentService paymentService;
    private final NotificationService notificationService;
    private final Logger logger = LoggerFactory.getLogger(OrderService.class);
    
    @Autowired
    public OrderService(
        OrderRepository orderRepository,
        PaymentService paymentService,
        NotificationService notificationService
    ) {
        this.orderRepository = orderRepository;
        this.paymentService = paymentService;
        this.notificationService = notificationService;
    }
    
    public Order createOrder(CreateOrderRequest request) {
        logger.info("Creating order for user: {}", request.getUserId());
        
        // Validation
        validateOrderRequest(request);
        
        // Business logic
        Order order = new Order();
        order.setUserId(request.getUserId());
        order.setTotal(calculateTotal(request.getItems()));
        order.setStatus(OrderStatus.PENDING);
        
        // Persistence
        Order savedOrder = orderRepository.save(order);
        
        // Side effects
        try {
            paymentService.processPayment(savedOrder);
            notificationService.sendOrderConfirmation(savedOrder);
        } catch (Exception e) {
            logger.error("Failed to process order side effects", e);
            throw new OrderProcessingException("Order created but processing failed", e);
        }
        
        return savedOrder;
    }
    
    private void validateOrderRequest(CreateOrderRequest request) {
        if (request.getItems().isEmpty()) {
            throw new ValidationException("Order must contain at least one item");
        }
    }
}

// Always:
// - Use constructor injection
// - Add @Transactional where needed
// - Validate inputs
// - Log important operations
// - Handle exceptions appropriately
```

**Example 3: Data Access Pattern (C#/EF Core)**
```markdown
## Repository Pattern

Follow this pattern for all data access:

public interface IOrderRepository
{
    Task<Order> GetByIdAsync(int orderId);
    Task<IEnumerable<Order>> GetByUserIdAsync(int userId);
    Task<Order> CreateAsync(Order order);
    Task UpdateAsync(Order order);
}

public class OrderRepository : IOrderRepository
{
    private readonly ApplicationDbContext _context;
    private readonly ILogger<OrderRepository> _logger;
    
    public OrderRepository(
        ApplicationDbContext context,
        ILogger<OrderRepository> logger)
    {
        _context = context;
        _logger = logger;
    }
    
    public async Task<Order> GetByIdAsync(int orderId)
    {
        try
        {
            return await _context.Orders
                .Include(o => o.OrderItems)
                .FirstOrDefaultAsync(o => o.Id == orderId);
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error fetching order {OrderId}", orderId);
            throw new DataAccessException($"Failed to fetch order {orderId}", ex);
        }
    }
    
    public async Task<Order> CreateAsync(Order order)
    {
        ArgumentNullException.ThrowIfNull(order);
        
        try
        {
            _context.Orders.Add(order);
            await _context.SaveChangesAsync();
            return order;
        }
        catch (DbUpdateException ex)
        {
            _logger.LogError(ex, "Error creating order");
            throw new DataAccessException("Failed to create order", ex);
        }
    }
}

// Always:
// - Define interfaces for repositories
// - Use async/await for database operations
// - Include proper error handling
// - Log data access operations
// - Validate inputs
// - Use Include() for eager loading
```

## Critical Limitations of Repository-Wide Instructions

**Evidence-Based Research**: Understanding these limitations is essential for setting realistic expectations.

### Token Limits and Context Windows

**Research Finding**: GitHub Copilot models have context windows between 8K-32K tokens, with part reserved for code context.

**Best Practice:**
- Keep repository instructions concise (preferably under 2KB)
- Focus on the most important patterns and standards
- Use clear, direct language
- Extremely large files may be truncated or partially ignored

### Non-Deterministic Behavior

**Research Finding**: Repository instructions "tilt" Copilot's suggestions but don't guarantee strict enforcement. Copilot may occasionally diverge due to the probabilistic nature of AI.

**Reality Check:**
- Instructions guide behavior, they don't control it absolutely
- Some suggestions may not follow instructions perfectly
- Code review is still necessary
- Update instructions when patterns don't work as expected

### Legacy Code Influence

**Research Finding**: Without clear instructions, Copilot dropped into a legacy codebase tends to replicate bad patterns seen in the repository.

**Solution:**
- Use deprecated patterns section to explicitly call out what not to do
- Consider path-specific instructions for legacy code areas
- Provide examples of correct patterns to override legacy influence

## Common Mistakes with Repository-Wide Instructions

**Evidence-Based Analysis**: These patterns have been identified in real-world case studies as ineffective.

### 1. Being Too Vague or Generic

**❌ Doesn't Work:**
```markdown
Write clean, maintainable code
Follow best practices
Use good coding standards
```

**✅ Works Better:**
```markdown
- Functions should be < 50 lines
- Extract complex logic into named helper functions
- Use TypeScript strict mode with explicit types
- Follow the existing patterns in `src/components/ui/`
```

**Research Insight**: Vague directives yield inconsistent results. Copilot needs specific, actionable guidance.

### 2. Overloading the Instructions File

**Research Finding**: Large, unfocused instruction files dilute Copilot's ability to synthesize productive suggestions.

**Best Practice:**
- Focus on the 20% of patterns that matter 80% of the time
- Remove outdated or rarely-used instructions
- Link to external documentation for deep details
- Keep the file under 2KB when possible

### 3. Not Updating Instructions

**Research Finding**: Instructions that reference obsolete dependencies or don't match current code cause Copilot to suggest broken solutions.

**Best Practice:**
- Review and update instructions with each major project change
- Remove deprecated patterns explicitly
- Test instructions by asking Copilot to generate code
- Version control allows tracking changes over time

### 4. Assuming Strict Enforcement

**Critical Mistake**: Expecting instructions to work like configuration files or linters.

**Reality:**
- Instructions are **guidance**, not rules
- Always review generated code
- Run linters and tests on Copilot-generated code
- Treat Copilot suggestions as drafts, not final code
- Use code review processes for all code

---

# Part 2: Path-Specific Instructions (`.github/instructions/*.instructions.md`)

## Why Path-Specific Instructions Matter

Path-specific instructions allow you to provide **granular, context-aware guidance** for different parts of your codebase. This is especially valuable for:

- **Monorepos** with different standards for different projects
- **Frontend vs Backend** with different technology stacks
- **Security-sensitive areas** requiring stricter patterns
- **Legacy code** that needs modernization guidance
- **Test files** with specific conventions
- **Different teams** working on different areas

## How Path-Specific Instructions Work

Path-specific instructions use the `applyTo` field to define which files they affect:

**File Structure:**
```
.github/
├── copilot-instructions.md              # Repository-wide instructions
└── instructions/
    ├── frontend.instructions.md         # Frontend-specific
    ├── backend-api.instructions.md      # Backend-specific
    ├── security.instructions.md         # Security areas
    └── tests.instructions.md            # Test files
```

**Example Files:**

**Example 1: API Layer** (`.github/instructions/api.instructions.md`):
```markdown
applyTo:
  - src/api/**
  - services/api/**
  - controllers/**

---

# API Layer Instructions

## REST API Standards
- Use RESTful conventions (GET/POST/PUT/PATCH/DELETE)
- Version APIs: /api/v1/resource
- Return consistent response format: { data, error, metadata }
- Use proper HTTP status codes (200, 201, 400, 401, 403, 404, 500)
- Implement pagination for list endpoints (limit, offset)
- Include request validation middleware

## Error Handling
- Return structured error responses: { error: { code, message, details } }
- Log errors with correlation IDs for tracing
- Never expose stack traces to clients
- Use problem details format (RFC 7807)

## Documentation
- Document all endpoints with OpenAPI/Swagger
- Include request/response examples
- Document authentication requirements
- List all possible status codes and their meanings
```

**Example 2: Database Layer** (`.github/instructions/database.instructions.md`):
```markdown
applyTo:
  - src/database/**
  - repositories/**
  - models/**
  - migrations/**

---

# Database Layer Instructions

## Data Access Patterns
- Use repository pattern for data access abstraction
- All database operations must be async
- Use transactions for multi-step operations
- Implement connection pooling
- Use prepared statements / parameterized queries always

## Query Optimization
- Add indexes for frequently queried columns
- Use SELECT specific columns, not SELECT *
- Limit result sets with pagination
- Use database-specific optimization hints when needed
- Profile slow queries and optimize

## Migrations
- Make migrations reversible when possible
- Test migrations on staging before production
- Include rollback scripts
- Document breaking changes
- Version migrations with timestamps
```

**Example 3: Infrastructure Code** (`.github/instructions/infrastructure.instructions.md`):
```markdown
applyTo:
  - terraform/**
  - infrastructure/**
  - *.tf
  - ansible/**

---

# Infrastructure-as-Code Instructions

## Terraform Standards
- Use modules for reusable components
- Define variables with descriptions and validation
- Use remote state with state locking
- Tag all resources (Environment, Owner, CostCenter)
- Use data sources instead of hard-coded values
- Implement lifecycle rules for critical resources

## Security Best Practices
- Never hard-code credentials or secrets
- Use secret managers (AWS Secrets Manager, Azure Key Vault)
- Enable encryption at rest and in transit
- Apply least privilege IAM policies
- Use private subnets for databases and internal services
- Enable audit logging (CloudTrail, Azure Monitor)

## Cost Optimization
- Right-size resources based on usage
- Use autoscaling where appropriate
- Implement resource lifecycle policies
- Tag resources for cost tracking
- Use cost analysis tools (Infracost)
```

## Best Practices for Path-Specific Instructions

### 1. Use Precise Path Globs

**Research Finding**: Incorrect path globs are the #1 reason path-specific instructions don't work.

**Best Practices:**
```markdown
✅ Good - Specific and testable:
applyTo:
  - src/frontend/**
  - components/ui/**/*.tsx

❌ Bad - Common mistakes:
applyTo:
  - frontend          # Missing /** for recursive match
  - /src/**           # Leading slash - don't use, paths are relative to repo root
  - *.tsx             # Missing path prefix, too broad
  - **/*.test.tsx     # Works but be aware it matches at all directory levels
```

**Test Your Globs:**
- Verify patterns match actual file paths in your repository
- Test with `find` command: `find . -path "src/frontend/**" -type f`
- Paths are relative to repository root (no leading slash needed)
- Use `**` for recursive directory matching
- Be specific to avoid unintended matches

### 2. Keep Instructions Focused and Relevant

**Evidence-Based Recommendation**: Path-specific instructions should only contain guidance relevant to that specific area.

**Example 4: Testing Standards** (`.github/instructions/tests.instructions.md`):
```markdown
applyTo:
  - **/*.test.*
  - **/*.spec.*
  - tests/**
  - test/**

---

# Testing Standards

## Test Structure
- Use Arrange-Act-Assert (AAA) pattern
- One test per behavior or scenario
- Descriptive test names that explain what's being tested
- Group related tests in describe/context blocks

## Coverage Requirements
- Minimum 80% coverage for business logic
- Minimum 60% coverage for data access layer
- 100% coverage for critical security functions
- Test happy paths and error cases

## Best Practices (Language-Agnostic)
- Test behavior, not implementation details
- Mock external dependencies (databases, APIs, file system)
- Don't mock internal code you're testing
- Use test fixtures and factories for test data
- Clean up test data after each test
- Make tests independent - can run in any order

## Examples by Framework

# Python (pytest)
def test_create_order_succeeds_with_valid_data():
    # Arrange
    order_service = OrderService(mock_repository)
    order_data = {"user_id": 1, "items": [{"id": 1, "quantity": 2}]}
    
    # Act
    result = order_service.create_order(order_data)
    
    # Assert
    assert result.status == "created"
    assert len(result.items) == 1

# Java (JUnit)
@Test
public void testCreateOrder_WithValidData_ReturnsCreatedOrder() {
    // Arrange
    OrderService orderService = new OrderService(mockRepository);
    OrderRequest request = new OrderRequest(1, items);
    
    // Act
    Order result = orderService.createOrder(request);
    
    // Assert
    assertEquals(OrderStatus.CREATED, result.getStatus());
    assertNotNull(result.getId());
}
```

### 3. Handle Conflicts with Repository-Wide Instructions

**Research Finding**: Path-specific and repository-wide instructions merge through context, not hierarchy.

**Best Practice:**
- Ensure path-specific instructions complement, not contradict, repository-wide instructions
- Use path-specific to add detail, not override basics
- Document intentional differences explicitly

**Example:**
```markdown
# backend-api.instructions.md
applyTo:
  - src/api/**
  - server/**

---

# Backend API Specific Instructions

Note: These instructions extend the repository-wide instructions with
backend-specific patterns. For general TypeScript and project standards,
see `.github/copilot-instructions.md`.

## API-Specific Patterns
- Use Express.js middleware pattern
- Implement request validation with Zod
- Return consistent error format: { error: string, code: number }
- Log all requests with structured logging
```

### 4. Use for Gradual Migration

**Real-World Use Case**: Use path-specific instructions to guide modernization of legacy code.

**Example** (`.github/instructions/legacy.instructions.md`):
```markdown
applyTo:
  - legacy/**
  - deprecated/**

---

# Legacy Code Modernization

When working with files in these directories:

## Current State
- These use class components and older patterns
- Do NOT replicate these patterns in new code

## When Modifying
- Suggest migration to functional components
- Flag usage of deprecated APIs
- Recommend modern alternatives
- Link to migration guide: /docs/modernization-guide.md

## Do Not
- Make breaking changes without team approval
- Remove code without understanding its purpose
- Introduce new dependencies to legacy code
```

## Common Mistakes with Path-Specific Instructions

### 1. Missing `applyTo` Section

**Critical Error**: Without `applyTo`, the instructions won't apply to any files.

**Fix:**
```markdown
❌ Wrong - No applyTo:
---
# Frontend Instructions
Use React hooks...

✅ Correct - Include applyTo:
applyTo:
  - src/frontend/**

---
# Frontend Instructions
Use React hooks...
```

### 2. Incorrect File Extension

**Research Finding**: Only files ending in `.instructions.md` are recognized.

**Fix:**
```
❌ Wrong:
.github/instructions/frontend.md
.github/instructions/frontend-instructions.md

✅ Correct:
.github/instructions/frontend.instructions.md
.github/instructions/backend-api.instructions.md
```

### 3. Glob Patterns Don't Match Files

**Most Common Issue**: Path globs that don't match actual file structure.

**Debug Steps:**
1. Test glob with `find`: `find . -path "./src/frontend/**"`
2. Check for leading slashes (often not needed)
3. Verify `**` for recursive matching
4. Ensure case sensitivity matches

### 4. Conflicting Instructions

**Problem**: Path-specific instructions that contradict repository-wide or each other.

**Example of Conflict:**
```markdown
# Repository-wide says:
Use TypeScript strict mode

# Path-specific says:
Use any type for quick prototyping

# Result: Confusing and unpredictable
```

**Fix**: Ensure instructions complement each other:
```markdown
# Path-specific should say:
Follow repository-wide TypeScript standards.
For prototyping in this area, use unknown instead of any.
```

### 5. Too Many Overlapping Instructions

**Research Finding**: Having many path-specific files with overlapping patterns dilutes effectiveness.

**Best Practice:**
- Limit to 3-5 path-specific instruction files
- Ensure each has a clear, distinct purpose
- Minimize overlap in `applyTo` patterns
- Test which instructions apply to key files

---

# Implementation Strategies

## For New Projects

**Evidence-Based Approach**: Starting with instructions from day one shows the highest return on investment.

### Phase 1: Repository-Wide Foundation (Week 1)
1. Create `.github/copilot-instructions.md`
2. Include:
   - Project overview and purpose
   - Technology stack with versions
   - Basic code style standards
   - Project structure

### Phase 2: Core Patterns (Week 2-3)
3. Add to repository-wide instructions:
   - Architecture patterns
   - Security requirements
   - Error handling standards
   - Testing expectations

### Phase 3: Path-Specific Refinement (Week 4+)
4. Create path-specific instructions for:
   - Test files (`tests.instructions.md`)
   - Frontend vs backend (if applicable)
   - Security-sensitive areas
5. Test and refine based on usage

## For Existing Projects

**Research Finding**: Gradual adoption with team input leads to better adoption and effectiveness.

### Step 1: Audit Current Patterns
- Review existing code to identify common patterns
- Document what's working well
- Identify inconsistencies to address

### Step 2: Start with Repository-Wide Basics
- Create `.github/copilot-instructions.md`
- Focus on:
  - Tech stack (prevent suggesting wrong frameworks)
  - Deprecated patterns (prevent replicating old code)
  - Project structure overview
- Test with team: ask Copilot to generate code

### Step 3: Add Path-Specific as Needed
- Identify areas with unique requirements
- Create targeted instruction files
- Start with 1-2 files, expand based on need

### Step 4: Iterate Based on Feedback
- Collect team feedback on what's working
- Refine instructions based on Copilot's output
- Remove ineffective instructions
- Update as project evolves

## Measuring Effectiveness

**Research-Backed Metrics**: Track these indicators to quantify impact.

### Qualitative Metrics:
- **Code Review Time**: Faster reviews due to consistent patterns?
- **Code Consistency**: New code following established patterns?
- **Onboarding Speed**: New developers productive faster?
- **Team Satisfaction**: Developers finding Copilot more helpful?

### Quantitative Metrics:
- **Review Cycle Time**: Days from PR creation to merge
- **Pattern Adherence**: % of code reviews with style comments
- **Copilot Acceptance Rate**: % of suggestions accepted
- **Bug Rate**: Issues per 1000 lines of code

### Example Tracking:
```markdown
## Repository Instructions Effectiveness Log

### November 2025
- Average PR review time: 4 hours (was 8 hours in October)
- Style-related review comments: 12% (was 35%)
- Copilot suggestion acceptance: 42% (was 28%)
- Team feedback: "Much more relevant suggestions"

### Actions Taken
- Added deprecated patterns section → reduced legacy pattern replication
- Created tests.instructions.md → better test generation
- Need to add more examples for API route patterns
```

## Maintaining Instructions

**Critical Success Factor**: Instructions are living documents requiring active maintenance.

### Regular Review Cadence

**Best Practice Schedule:**
- **Monthly**: Quick review of effectiveness metrics
- **Quarterly**: Deep review with team feedback session
- **After Major Changes**: Update immediately when architecture changes
- **During Onboarding**: Get feedback from new team members

### Update Triggers

Update instructions when:
- ✅ New major technology is adopted
- ✅ Architectural patterns change
- ✅ Security requirements evolve
- ✅ Team consistently asks the same questions
- ✅ Code review patterns emerge
- ✅ Copilot generates unexpected code
- ✅ Project structure changes significantly

### Feedback Process

**Template for Collecting Feedback:**
```markdown
## Instructions Feedback Form

**Date**: 2025-11-03
**Contributor**: [Name]
**Area**: [ ] Repository-wide  [ ] Path-specific: ___________

**What's Not Working?**
[Describe the issue or unclear guidance]

**Suggested Improvement:**
[What should be changed or added?]

**Impact Level:**
[ ] Daily - affects me constantly
[ ] Weekly - I encounter this regularly  
[ ] Monthly - occasional issue
[ ] Rare - but important

**Example:**
[Link to PR or code where this came up]
```

### Version Tracking

**Best Practice:**
```markdown
---
# .github/copilot-instructions.md
version: 2.1.0
last-updated: 2025-11-03
maintainer: Development Team
---

## Changelog
- v2.1.0 (2025-11-03): Added path-specific instructions for tests
- v2.0.0 (2025-10-15): Migrated from Pages Router to App Router
- v1.5.0 (2025-09-20): Added security requirements section
- v1.0.0 (2025-08-01): Initial repository instructions
```

---

# Summary & Key Takeaways

## Repository-Wide vs Path-Specific Instructions

| Aspect | Repository-Wide<br>(`.github/copilot-instructions.md`) | Path-Specific<br>(`.github/instructions/*.instructions.md`) |
|--------|---------------------------------------------------|--------------------------------------------------|
| **Scope** | All files in repository | Only files matching `applyTo` globs |
| **Purpose** | Universal standards & tech stack | Context-specific guidance |
| **Number of Files** | One file | Multiple files (3-5 recommended) |
| **Size Recommendation** | < 2KB | < 1KB each |
| **Update Frequency** | Quarterly or on major changes | As specific areas evolve |
| **Best For** | Project foundations | Specialized requirements |
| **Complexity** | Simple - no `applyTo` needed | More complex - requires glob patterns |

## Evidence-Based Impact

**Research shows well-implemented repository instructions deliver:**
- 50%+ increase in coding productivity
- 3-4x faster feature delivery
- 60% reduction in code review cycles
- Improved onboarding experience
- Higher code consistency
- Reduced technical debt

**Critical Success Factors:**
1. Specificity over vagueness
2. Regular maintenance and updates
3. Team collaboration and buy-in
4. Realistic expectations about AI limitations
5. Always review generated code

## Top 10 Dos and Don'ts

### ✅ DO:
1. **Be specific** - "Use Next.js App Router" not "use modern patterns"
2. **Provide examples** - Show actual code patterns you want
3. **Document deprecated patterns** - Explicitly say what NOT to do
4. **Keep it concise** - Under 2KB for repo-wide, under 1KB for path-specific
5. **Use `applyTo` correctly** - Test your glob patterns
6. **Update regularly** - Review quarterly and after major changes
7. **Test instructions** - Ask Copilot to generate code, verify results
8. **Version track** - Use changelog to document evolution
9. **Collect feedback** - Get input from team members
10. **Complement, don't conflict** - Ensure instructions work together

### ❌ DON'T:
1. **Be vague** - "Write good code" provides no guidance
2. **Overload files** - Don't create encyclopedia-length instructions
3. **Forget `applyTo`** - Path-specific instructions need glob patterns
4. **Let them stagnate** - Outdated instructions cause bad suggestions
5. **Expect strict enforcement** - Instructions guide, not control
6. **Create too many files** - Limit to 3-5 path-specific files
7. **Use wrong extensions** - Must end in `.instructions.md`
8. **Skip testing** - Always verify instructions work as expected
9. **Create conflicts** - Ensure instructions complement each other
10. **Trust blindly** - Always review Copilot's generated code

## Quick Start Checklist

### Creating Your First Repository Instructions

- [ ] Create `.github/copilot-instructions.md`
- [ ] Add project overview (what, who, why)
- [ ] Define technology stack with versions
- [ ] Document project structure
- [ ] List coding style standards
- [ ] Add security requirements
- [ ] Document deprecated patterns
- [ ] Provide code examples
- [ ] Keep under 2KB total
- [ ] Test by asking Copilot to generate code
- [ ] Get team feedback
- [ ] Iterate and refine

### Adding Path-Specific Instructions (Optional)

- [ ] Identify areas needing specific guidance
- [ ] Create `.github/instructions/` directory
- [ ] Create first file: `{area}.instructions.md`
- [ ] Add `applyTo:` with glob patterns
- [ ] Test glob patterns match intended files
- [ ] Keep instructions focused and relevant
- [ ] Ensure no conflicts with repo-wide instructions
- [ ] Test with actual files in that path
- [ ] Limit to 3-5 files total
- [ ] Document why each file exists

## Conclusion

Repository custom instructions are a powerful tool for guiding Copilot, but they work best when:

1. **Focused on the repository** - Not user preferences
2. **Clearly structured** - Repository-wide for foundations, path-specific for nuance
3. **Specific and actionable** - Not vague or generic
4. **Regularly maintained** - Updated as the project evolves
5. **Realistic about limitations** - Guidance, not enforcement

**Remember**: Instructions guide Copilot's behavior—they don't control it absolutely. Always review generated code, run tests, and use your judgment. Copilot is a powerful assistant that works best with clear guidance, but it's not a replacement for human expertise and code review.

The combination of well-crafted repository-wide instructions and targeted path-specific instructions creates an environment where Copilot can provide relevant, context-aware suggestions that truly accelerate development while maintaining code quality and consistency.

---

## Additional Resources

### Official Documentation
- [Adding Repository Custom Instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions)
- [Path-Scoped Custom Instruction Files](https://github.blog/changelog/2025-09-03-copilot-code-review-path-scoped-custom-instruction-file-support/)
- [GitHub Copilot Tutorials](https://docs.github.com/copilot/tutorials)

### Best Practices & Research
- [5 Tips for Writing Better Custom Instructions (GitHub Blog)](https://github.blog/ai-and-ml/github-copilot/5-tips-for-writing-better-custom-instructions-for-copilot/)
- [The Complete Guide to GitHub Copilot Instructions](https://www.copilotcraft.dev/blog/getting-started-github-copilot-instructions)
- [Everything About Copilot Instructions (DEV Community)](https://dev.to/anchildress1/everything-i-know-about-github-copilot-instructions-from-zero-to-onboarded-for-real-4nb0)
- [All I've Learned About Copilot Instructions (DEV Community)](https://dev.to/anchildress1/all-ive-learned-about-github-copilot-instructions-so-far-5bm7)

### Common Problems & Solutions
- [Common Problems with GitHub Copilot](https://hackernoon.com/common-problems-with-github-copilot-and-how-to-solve-them)
- [GitHub Copilot Best Practices](https://www.coderabbit.ai/blog/github-copilot-best-practices-10-tips-and-tricks-that-actually-help)
