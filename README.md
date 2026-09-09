# Radar Investe São Carlos

MVP em FastAPI + SQLite para acompanhar somente oportunidades de investimento ainda abertas.

## Rodar

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m uvicorn main:app --reload
```

Abra http://127.0.0.1:8000

## Atualização automática inicial

O botão **Atualizar fontes** consulta as páginas oficiais de chamadas abertas da FAPESP e FINEP, tenta extrair nome, prazo, público, valor quando disponível e link, e remove do banco itens vencidos.

Como páginas públicas podem alterar o HTML, o sistema foi construído para não derrubar o painel quando uma fonte falhar: ele continua operando e permite cadastro manual.


## Versão 3 - Transferegov

O botão **Atualizar fontes** também consulta o arquivo oficial diário de **Programas Disponibilizados** do Transferegov.
O coletor mantém somente programas com prazo de proposta em aberto e filtra assuntos ligados a comércio, desenvolvimento econômico, indústria, empreendedorismo, startups, tecnologia e inovação.

Fonte usada pelo sistema:
- `https://repositorio.dados.gov.br/seges/detru/siconv_programa.csv.zip`

Observação: quando o arquivo federal não traz valor disponível em uma coluna estruturada, o card mostra **Consultar edital/programa**, em vez de inventar um valor.
