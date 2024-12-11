# Extrator-de-Dados-01
Este repositório contém uma solução automatizada para a coleta e organização de dados importantes de clientes. O processo é executado anualmente, com os dados sendo extraídos, processados e organizados de planilhas Excel preenchidas mensalmente.
Nesse arquivo, eu queria extrair dados dos clientes que não responderam mais as mensagens no Whatsapp, bem como: Telefones de contato e Link's que os direcionaram para iniciar uma conversa. (Você pode adaptar as colunas)

![image](https://github.com/user-attachments/assets/8d157b08-e00a-4f6b-b332-2cfe24494384)


Nesse processo eu utilizei as colunas com nomes específicos. Porém caso necessite a alteração, pode mudar as varíaveis e adapta-lás para os quais você utiliza:

            for coluna in aba.columns:
                col_amostra = aba[coluna].astype(str).dropna().head(10).str.lower()

                if col_telefone is None and col_amostra.str.contains('telefone|contato').any():
                    col_telefone = coluna
                elif col_resposta is None and col_amostra.str.contains('/').any():
                    col_resposta = coluna
                elif col_link is None and col_amostra.str.contains('http|www').any():
                    col_link = coluna 

Uma outra situação, é a filtragem dos dados, que também está com os nomes das variavéis que eu utilizei nos arquivos .xlsx
Você pode adapta-lós com as variáveis que você utiliza: 

               filtro_nao_respondido = aba[aba[col_resposta].str.strip() == '/']
                for _, linha in filtro_nao_respondido.iterrows():
                    telefones_nao_respondidos.append(linha[col_telefone])
                    links_nao_respondidos.append(linha[col_link])
            else:print(f"Aba '{aba_nome}' no arquivo '{arquivo}' não possui todas as colunas necessárias. "
                      f"Telefone: {col_telefone}, Resposta: {col_resposta}, Link: {col_link}")

Você pode também eliminar as funções de print para monstrar os dados e onde está sendo analisado, pois assim, faz a exclusão de dados inerentes á sua pesquisa como o exemplo abaixo: 

![image](https://github.com/user-attachments/assets/15f9b868-b881-40da-b76a-764523350293)

Indico que se o uso do código for pelo Collab, fazer o upload das planilhas no ambiente. Copiar o caminho e inserir no campo indicado.

     pasta_planilhas = "Insira o caminho aqui"
     arquivos = [arquivo for arquivo in os.listdir(pasta_planilhas) if arquivo.endswith('.xlsx')]


Por fim, agradeço a leitura dos pontos citados. Espero que esteja claro como utilizar. 

Fico á disposição em qualquer dúvida referente á este reporitório. Você pode falar comigo pelo e-mail: adri.bill.cam@gmail.com






