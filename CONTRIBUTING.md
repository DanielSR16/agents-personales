# Contributing to Agents Personales

¡Gracias por tu interés en contribuir a este proyecto! Este documento proporciona guías y normas para contribuir.

## 🚀 Getting Started

1. **Fork el repositorio**
   ```bash
   git clone https://github.com/DanielSR16/agents-personales.git
   cd agents-personales
   ```

2. **Instala dependencias**
   ```bash
   npm install
   ```

3. **Crea una rama para tu feature**
   ```bash
   git checkout -b feature/tu-feature
   # o para bugfixes
   git checkout -b fix/tu-bugfix
   ```

## 📋 Proceso de Contribución

### 1. Desarrollo

- Mantén el código limpio y bien documentado
- Sigue las convenciones de código existentes
- Usa TypeScript cuando sea posible
- Agrega ejemplos de uso en comentarios

### 2. Testing

```bash
npm test
```

Asegúrate de que:
- Todos los tests pasen
- Agregues tests para nuevas funcionalidades
- Mantengas o mejores la cobertura

### 3. Linting y Formatting

```bash
npm run lint
npm run format
```

### 4. Commit Messages

Usa mensajes de commit claros y descriptivos siguiendo el formato:

```
<type>: <description>

<optional-body>

<optional-footer>
```

**Types:**
- `feat`: Nueva funcionalidad
- `fix`: Corrección de bug
- `docs`: Cambios en documentación
- `style`: Formato/linting (sin cambios de código)
- `refactor`: Refactorización de código
- `perf`: Mejoras de performance
- `test`: Agregación de tests
- `chore`: Cambios en build, deps, etc

**Ejemplos:**
```
feat: add useActionState hook to form component

fix: correct async middleware error handling in Express 5

docs: update React 19 Server Components guide
```

### 5. Pull Request

Al abrir un PR, asegúrate de:

1. **Descripción clara:**
   - Qué cambias y por qué
   - Referencias a issues (#123)
   - Cambios breaking si aplica

2. **Checklist:**
   - [ ] Tests added/updated
   - [ ] Documentation updated
   - [ ] No breaking changes (o well documented)
   - [ ] Linting passes (`npm run lint`)
   - [ ] Formatting passes (`npm run format`)

3. **Ejemplo:**
   ```markdown
   ## Description
   Adds support for React 19 Server Components to the Frontend Agent
   
   ## Related Issues
   Closes #15
   
   ## Changes
   - Updated Frontend Agent tools
   - Added `createServerComponent` tool
   - Added Server Component examples
   
   ## Testing
   Tested with React 19.2.0+
   ```

## 🎯 Guías por Área

### Backend Agent (Express 5)

- Usa async/await en lugar de callbacks
- Implementa error handling centralizado
- Valida inputs con schemas (Zod/Yup)
- Usa TypeScript para type safety

**Ejemplo:**
```typescript
export async function setupErrorHandling(app: Express) {
  app.use((err: Error, req: Request, res: Response, next: NextFunction) => {
    console.error(err.stack);
    res.status(500).json({ error: err.message });
  });
}
```

### Frontend Agent (React 19)

- Prefiere Server Components por defecto
- Usa Client Components solo cuando sea necesario ("use client")
- Implementa useActionState para formularios
- Usa TypeScript para componentes

**Ejemplo:**
```typescript
// Server Component
export async function UserList() {
  const users = await fetchUsers();
  return (
    <div>
      {users.map(user => <UserCard key={user.id} user={user} />)}
    </div>
  );
}

// Client Component
'use client';
export function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

### Styling (Tailwind CSS v4)

- Usa CSS-first configuration con @theme
- Aprovecha colores OKLCH
- Usa container queries para componentes responsivos
- Documenta clases personalizadas

**Ejemplo:**
```css
@import "tailwindcss";

@theme {
  --color-brand-500: oklch(0.6 0.2 250);
  --font-display: "Satoshi", "sans-serif";
}
```

## 📚 Actualizando Documentación

Si cambias o agregas features:

1. Actualiza el `README.md` en el agente correspondiente
2. Agrega ejemplos de uso
3. Documenta cambios breaking
4. Usa Context7 para información actualizada

## 🔍 Code Review

Los maintainers revisarán tu PR y pueden pedir cambios. Por favor:

- Responde a los comentarios
- Actualiza tu PR con los cambios solicitados
- Haz force-push solo si es necesario (después de acuerdos)

## 📖 Recursos Útiles

- **Express 5 Docs:** https://expressjs.com
- **React 19 Docs:** https://react.dev
- **Tailwind CSS v4:** https://tailwindcss.com
- **Context7:** Para documentación actualizada de librerías

## ❓ Preguntas o Dudas

Abre una issue para:
- Reportar bugs
- Sugerir nuevas features
- Hacer preguntas sobre el proyecto
- Discutir decisiones de design

## 📝 Código de Conducta

Este proyecto adopta un Código de Conducta. Se espera que todos los contribuyentes:

- Sean respetuosos y constructivos
- Eviten lenguaje discriminatorio
- Acepten crítica constructiva
- Enfoquen en lo que es mejor para el proyecto

Gracias por contribuir! 🎉
