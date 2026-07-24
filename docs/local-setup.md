# Validación local

El registro npm de este entorno devuelve `403` para tarballs y deja `node_modules` incompleto. Para probar localmente:

```bash
rm -rf node_modules package-lock.json
npm install
cp .env.example .env.local
printf 'DATABASE_URL="postgresql://postgres:postgres@localhost:5432/asesoria_store?schema=public"\n' >> .env.local
npm run db:generate
npm run db:migrate -- --name init
npm run lint
npm run build
npm run dev
```
