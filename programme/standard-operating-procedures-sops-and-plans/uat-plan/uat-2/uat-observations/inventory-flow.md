# Inventory Flow

| S .No | Tipo de registo   | Caso de utilização (com base no âmbito de aplicação assinado)                                                                                                                                                                                                                                                                                                                                                              | Etapas a executar                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Resultado esperado                                                                                                                      | Observação (aprovação/reprovação)   | Comentário                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | eGov@1234                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                     |
| ----- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1     | Gestor de armazém | É gestor de um armazém no posto administrativo A e recebeu hoje no seu armazém comunitário um stock de 2 fardos provenientes de um armazém distrital em Angónia. Registe a recepção desta mercadoria na aplicação.                                                                                                                                                                                                         | <p>1. iniciar sessão como gestor de armazém<br>2. Clique em gerir stock<br>3. Clique em registar a entrada em armazém<br>4. Introduzir os dados do armazém gerido<br>5. Clicar em seguinte<br>7. Introduzir os dados da entrada em armazém - inclui os dados do armazém e o modo de proveniência dos fardos.<br>9. Clique no botão Submeter<br>9. Registo criado com êxito<br></p>                                                                                                                        | O gestor de armazém deve ser capaz de criar o registo de entrada de existências.                                                        | <p>Aprovado com comentarios<br></p> | <p>Apagar campo de aldeia na pagina inicial<br>Todos os Campos obrigatorios na primeira pagina (Pagina OU)<br>Registar guia de remessa = Registo de entradas<br>PPM, Provincia, outro Distrito, CPN - Trocar registo de entradas<br>Campo de data deve permetir editar<br>Trocar area administrativa por Unidade organizacional(label)<br>No armazem deve fazer Dropdown para aparecer a lista do armazem<br>Trocar armazem fornecedor por proviniencia (PPM, Provincia, outro Distrito, CPN devem ser opcoes do Dropdown)<br>Trocar as posicoes( armazem fornrcdor, numero da guia da remessa, tipo de transporte, matricula de veiculo, numero de redes na guia de remessa, numero de redes mosquiteiras recebidas)`<br>Tipo de trasnporte - retirar Estivador e barco e rever a nomeclatura da viatura (Cabine dupla)<br>Devemos ter um campo de "Esta em conformidade?" (fazer lista de Dropdwn com Sim ou Nao, e se Nao deve abrir um campo para comentar)<br>Sempre que ter uma diferenca entre redes recebidas e redes na guia de remessa, deve abrir um campo de comentarios para escrever o que esta acontecer (nomeado Comentario)<br><br></p> | <p>Mudar em TODAS as fichas label de Data de Recepcao para Data de Movimento<br>Saidas<br>-Mudar Detalhe das Accoes Emitidas por Detalhe do Movimento<br>-Mudar label de Armazem por "Destino"<br>-Trocar as posicoes(Destino, numero da guia da remessa, tipo de transporte, matricula de veiculo, numero de redes na guia de remessa)<br>-apagar campo de numero de redes mosquiteiras enviadas e campo de comentario<br>-Tipo de transporte - remover apenas opcao de Estivador<br>-Opcoes para destino (em ordem): Armazens satelite, monitor local, Outro armazem distrital, Armazem Provincial, Outra Provincia, CPN<br>-armazem datelite or monitor local, abrir campo com opcoes de todos os AS ou MLs nesse distrito<br>-Campo de matriculas de veiculos deve aceitar letras mayusculas</p> | <p>Delete village field on the start page<br>All required fields on the first page (Page OR)<br>Register delivery note = Register entries<br>PPM, Province, other District, CPN - Change Entry Register<br>Date field must allow edit<br>Change administrative area to Organizational Unit(label)<br>In the warehouse you must Dropdown to display the warehouse list<br>Change supplier warehouse by province (PPM, Province, other District, CPN should be Dropdown options)<br>Change positions (supplying warehouse, delivery note number, transport type, vehicle registration, number of nets on delivery note, number of received nets)<br>Type of transport - remove Stevedore and boat and revise the name of the vehicle (Double Cab)<br>We must have a field of Is this in conformity?" (make Dropdown list with Yes or No, and if No you must open a field to comment)<br><br>Whenever you have a difference between received nets and nets on the delivery tab, you must open a comment field to write what is happening (named Comment)</p> | <p>"Change on ALL tabs label from Date of Receipt to Date of Movement<br>Exits<br>-Change Actions Issued Detail for Movement Detail<br>-Change label of Warehouse by "Destination<br>-Change positions (Destination, delivery note number, transport type, vehicle license plate, net number on delivery note)<br>-delete the field of the number of mosquito nets sent and the comment field<br>-Type of transport - remove only Stevedore option<br>-Options for destination (in order): Satellite warehouse, local monitor, Other district warehouse, Provincial warehouse, Other province, CPN<br>-Satellite warehouse or local monitor, open field with options of all AS or MLs in that district<br>-Field for vehicle license plates must accept capital letters".</p> | <p>min is localidade and not until village<br><br>Change name ---reg guida de remesse - Registo de Entradas<br>Subtext - Registo De Entradas no Armazem<br><br>Change Texto de pesquisa de facilidas--> Nome do Armazem<br><br>Explore possibility of w/h selection similar to boundary selection tree OR link waybill code with w/h names and populate only those w/hs name associated with that waybill no.<br><br>comments when you receive mandatory<br>comments when you send --> optional<br><br>remove estivadores, barco.. rename cabina-->cabine<br><br>date for all 3 forms should be editable, but only past dates,,not future</p> | <p>Subtext in Saidas - Registar aviamentos feitos pelo armazem<br>Subtext in devolucoes - Registar devolucoes feitas ao armazem</p> |
| 2     | Gestor de armazém | É gestor de armazém do posto administrativo A e recebeu um stock de 45 mosquiteiros da equipa de distribuição. Registe na aplicação a recepção desta encomenda no armazém comunitário que gere como uma devolução.                                                                                                                                                                                                         | <p>1. iniciar sessão como gestor de armazém<br>2. Clique em gerir stock<br>3. Clicar em stock devolvido<br>4. Introduza os dados do armazém gerido por si.<br>5. Introduza os dados das existências que foram devolvidas - inclui o modo de transporte pelo qual as existências foram devolvidas e os dados do armazém de onde foram devolvidas.<br>6. Clique em Submeter<br>7. Registo criado com sucesso.<br><br></p>                                                                                   | O gestor de armazém deve poder registar as existências devolvidas depois de introduzir os dados no formulário "Existências devolvidas". | <p>Aprovado com comentarios<br></p> | <p>Data de recepcao para Data de Movimento<br>-Opcoes para origem: Monitor Local e Armazem Satelite (garantir que NA nao seja opcao)<br>-Se escolher monitor / armazem, abrir u campo novo que contenha todos os monitores / todos os armazens satelites existentes nesse distrito<br>-Trocar as posicoes (origem, numero da guia da remessa, tipo de transporte, matricula de veiculo, numero de redes na guia de remessa, quantidade de redes mosquiteiras devolvidas)<br>-Devemos ter um campo de "Esta em conformidade?" (fazer lista de Dropdwn com Sim ou Nao, e se Nao deve abrir um campo para comentar)<br>-Sempre que ter uma diferenca entre redes recebidas e redes na guia de remessa, deve abrir um campo de comentarios para escrever o que esta acontecer (nomeado Comentario)<br></p>                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | <p>Date of Receipt for Date of Movement<br>-Options for source: Local Monitor and Satellite Warehouse (make sure NA is not an option)<br>-If you choose monitor / warehouse, open a new field that contains all monitors / satellite warehouses in that district<br>-Change positions (origin, delivery note number, type of transport, vehicle license plate, number of nets on delivery note, quantity of mosquito nets returned)<br>-We must have a field for "Is this in conformity?" (make Dropdwn list with Yes or No, and if No you must open a field to comment)<br>-Every time you have a difference between nets received and nets on the delivery note, you must open a comment field to write what is happening (named Comment)<br></p>                                                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Conformity to consider fo Gp5. for gp4 focus on training                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                                                                                                     |
| 3     | Gestor de armazém | <p>"Está a inspeccionar o armazém no final do dia como gestor de um armazém satélite e contou o número de redes em stock no final do dia.<br><br>Como é que vai fazer um registo para os seguintes casos?<br><br>Há mais 50 redes no armazém que o utilizador contou do que o número de redes sugerido pelo sistema<br>Há menos 10 redes no armazém que foram contadas do que o número de redes sugerido pelo sistema"</p> | <p>"1. iniciar sessão como gestor de armazém<br>2. Clicar em gerir stocks<br>3. clicar em reconciliação de existências no ecrã inicial<br>4. Verificar o número total de mosquiteiros sugerido para o armazém (total de entradas - total de saídas = stock disponível)<br>5. Introduzir a contagem física 50 superior à contagem total sugerida.<br>6. Introduzir a razão, nos comentários, para a introdução de um maior número de existências no armazém<br>7. clicar no botão "Submeter".<br><br>"</p> | O gestor de armazém deve poder registar as existências de acordo com a contagem manual em vez da contagem das existências sugerida.     | <p>aprovado com comentarios<br></p> | <p>Existencias = Entradas + Devolucoes - Saidas<br>-Se o numero de inventario manual ser diferente as existencias de acordo com a formula, deve abrir o campo de comentario que seja obrigatorio<br>-Se os numeros sao iguais, campo de "Estao em conformidade?" com dropdown Sim ou Nao, e se for Nao, abrir campo para comentar obrigatoriamente.<br>-e possivel ter discrepancia e nao estar em conformidade ao mesmo tempo</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | <p>"Existences = Entries + Returns - Exits<br>-If the manual inventory number is different from the inventories according to the formula, you must open the comment field that is mandatory<br>-If the numbers are equal, the field "Are they in conformity?" with dropdown "Yes" or "No", and if it is "No", open the comment field.<br>- "It is possible to have discrepancy and not be in conformity at the same time".</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                     |
| 4     | Gestor de armazém | <p>É gestor de um armazém distrital e distribuiu o seguinte<br><br>200 redes à equipa de entregas A<br>5 fardos para o armazém satélite A<br><br>Efectue entradas para estas distribuições</p>                                                                                                                                                                                                                             | <p>"1. iniciar sessão como gestor de armazém<br>2. Clicar em gerir stocks<br>3. clicar em reconciliação de existências no ecrã inicial<br>4. Verificar o número total de mosquiteiros sugerido para o armazém (total de entradas - total de saídas = stock disponível)<br>5. Introduzir a contagem física mais 10 do que a contagem total sugerida.<br>6. Introduzir a razão, nos comentários, para a introdução de um número inferior de existências no armazém<br>7. clicar no botão "Submeter".</p>    | O gestor de armazém deve poder registar as existências de acordo com a contagem manual em vez da contagem das existências sugerida.     |                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | <p>Change in ALL the tabs label from Date of Receipt to Date of Movement<br>Exits<br>-Change Actions Issued Detail for Movement Detail<br>-Change label of Warehouse by "Destination<br>-Change positions (Destination, delivery note number, transport type, vehicle license plate, net number on delivery note)<br>-delete the field of the number of mosquito nets sent and the comment field<br>-Type of transport - remove only Stevedore option<br>-Options for destination (in order): Satellite warehouse, local monitor, Other district warehouse, Provincial warehouse, Other province, CPN<br>-Satellite warehouse or local monitor, open field with options of all AS or MLs in that district<br>-Field for vehicle license plates must accept capital letters.</p>                                                                                                                                                                                                                                                                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                     |
| 5     | Gestor de armazém | Sincronizar todos os registos pendentes de serem sincronizados na aplicação.                                                                                                                                                                                                                                                                                                                                               | Clique no botão de sincronização no ecrã inicial                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Todos os registos pendentes são sincronizados                                                                                           |                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                     |