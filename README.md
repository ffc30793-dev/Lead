# LeadFinder Backend

Arquitetura recomendada:

Frontend -> Cloud Function/API própria -> provedor de dados -> normalização -> Firestore -> frontend.

Regras importantes:
- Nunca exponha API keys de provedores de leads no navegador.
- Valide o usuário no servidor.
- Desconte créditos no servidor usando uma transação atômica.
- Aplique rate limiting.
- Valide webhook da Cakto antes de liberar plano/créditos.
- Normalize e deduplicate leads antes de salvar.

Endpoints sugeridos:
POST /search-leads
POST /webhooks/cakto
GET /plans
GET /me
POST /leads/:id/save

Variáveis de ambiente sugeridas:
LEADS_API_KEY=
LEADS_API_URL=
CAKTO_WEBHOOK_SECRET=
FIREBASE_PROJECT_ID=

O frontend deste pacote usa dados DEMO locais somente para demonstrar a interface. Substitua mockResults() em js/leads.js pela chamada ao backend real.