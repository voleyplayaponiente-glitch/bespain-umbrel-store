# BESPAIN — Tienda personal de apps de Umbrel

Community app store de Umbrel. Para usarla, en Umbrel: **App Store → ⋯ →
Community App Stores → Add** y pegar la URL de este repositorio.

## Aplicaciones

### Gestor Laboral
Cuadrantes y control de horas del personal. Puerto 3000.

La imagen se construye desde
[clauderoutine](https://github.com/voleyplayaponiente-glitch/clauderoutine)
(rama `claude/labor-management-scheduling-app-jd2hcj`) y se publica en
`ghcr.io/voleyplayaponiente-glitch/gestor-laboral`.

### Gestión Financiera
Contabilidad, tesorería, deudas y presupuesto del grupo. Puerto 3011.

Son **dos** imágenes, construidas desde el mismo repositorio (rama
`claude/tournament-bracket-manager-gvrcdt`, carpeta `finanzas/`):

- `ghcr.io/voleyplayaponiente-glitch/gestor-finanzas` — la aplicación (nginx)
- `ghcr.io/voleyplayaponiente-glitch/gestor-finanzas-api` — el almacén de copias

nginx sirve la app y pasa `/api` al almacén, de modo que **los dos comparten
dirección**. Eso es lo que permite que las copias de seguridad funcionen dentro
de casa sin HTTPS, sin CORS y sin túneles — el problema que aparecía cuando la
app se usaba desde GitHub Pages y el servidor estaba aquí.

La contraseña que Umbrel muestra para la app es el secreto que se escribe en
**Copias de seguridad → Copias en tu servidor**; la URL es la de la propia app.

Las copias quedan en `app-data/bespain-gestor-finanzas/copias/<empresa>/<fecha>.json`,
en texto plano y con checksum: se pueden abrir, copiar a otro disco o restaurar
a mano sin depender de nada.
