# NestJS Learning Notes

---

## Architecture

- Nest provides **out-of-the-box application architecture** for:
  - Highly **testable** apps
  - **Scalable** apps
  - **Loosely coupled** design
  - **Easily maintainable** code

## Controllers

- **Controllers must be registered in a Module** (e.g. add to the module’s `controllers` array).
- **Avoid library-specific approaches** in controllers (e.g. don’t use `@Res()` — that’s Express-specific).
- Prefer Nest’s built-in response handling so the app stays framework-agnostic.

## Providers

- **Providers** are a core concept in Nest. **Provider ≠ service** — “provider” is the general idea; a service is one kind of provider.
- **Examples of providers:** services, repositories, factories, helpers (any injectable class).
- Main idea: a provider can be **injected as a dependency**, so objects can relate to each other.
- **Wiring** of these objects is handled by the Nest runtime (dependency injection).

### Provider registration

- Providers (and controllers) must be **registered in a Module** via the `providers` and `controllers` arrays.

```ts
@Module({
  controllers: [CatsController],
  providers: [CatsService],
})
export class AppModule {}
```

## HTTP server

- Nest uses robust HTTP server frameworks:
  - **Express** (default)
  - **Fastify** (optional, can be configured)
