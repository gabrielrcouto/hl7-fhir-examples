# HL7 FHIR - Exemplos

Esse é um repositório com alguns exemplos, voltados para o público brasileiro, que usam o padrão HL7 FHIR.

## Configurando o ambiente

Você precisará ter instalado em seu computador o [Docker](https://www.docker.com/products/docker-desktop) e o [Docker Compose](https://docs.docker.com/compose/install/) para executar o servidor [HAPI FHIR](https://hapifhir.io/hapi-fhir/docs/server_jpa/introduction.html) localmente, digitando em seu terminal:

```bash
# para criar um volume, que vai permitir derrubar e subir o servidor sem perder dados
docker volume create hapi-data
docker-compose up
```

## Usando

### Fluxo Ind. Farmacêutica > VISA > Instituição de Saúde

Imagine que uma indústria farmacêutica deseja solicitar o registro de um produto na Agência Reguladora (VISA). Para isso, ela acessa um portal (registrar-produto.html).

Quando um produto é registrado, são enviados os seguintes recursos FHIR (dentro de um Bundle):

- MedicinalProduct
- MedicinalProductIngredient
- MedicinalProductPharmaceutical

Após o pedido de registro, um agente da VISA faz a verificação e autoriza a comercialização do produto (autorizar-produto.html). É enviado o seguinte recurso FHIR para essa ação:

- MedicinalProductAuthorization

Em uma instituição que está usando um S-RES, é solicitado a um farmacêutico que identifique se existem interações medicamentosas nos novos produtos autorizados. Ele então acessa o sistema (registrar-interacao.html), onde marca as interações, enviando o seguinte recurso FHIR (dentro de um Bundle):

- MedicinalProductInteraction

Um médico, ao atender um paciente, necessita fazer uma prescrição (prescrever.html). Ao prescrever, ele recebe um alerta, avisando que dois medicamentos possuem interação medicamentosa, evitando assim, um erro de prescrição.

## Créditos

[@gabrielrcouto](http://www.twitter.com/gabrielrcouto)

## Licença

[MIT License](http://gabrielrcouto.mit-license.org/)