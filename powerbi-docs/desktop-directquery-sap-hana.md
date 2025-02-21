---
title: DirectQuery para SAP HANA no Power BI
description: Considerações ao usar o DirectQuery com SAP HANA
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9d7c5415d084ea7ca9b6a6dd4da3e84662fc6349
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61303756"
---
# <a name="directquery-and-sap-hana"></a>DirectQuery e SAP HANA
Você pode se conectar a fontes de dados do **SAP HANA** diretamente usando o **DirectQuery**. Há duas opções ao se conectar ao SAP HANA:

* **Tratar o SAP HANA como uma fonte de dados multidimensional (padrão):**  Nesse caso, o comportamento será semelhante a quando o Power BI conecta-se a outras fontes multidimensionais, como SAP Business Warehouse ou Analysis Services. Ao se conectar ao SAP HANA usando essa configuração, um único analítico ou cálculo é selecionado e todas as medidas, hierarquias e atributos dessa exibição estará disponíveis na lista de campos. Conforme os visuais são criados, os dados de agregação serão sempre recuperados do SAP HANA. Essa é a abordagem recomendada e é o padrão para novos relatórios DirectQuery no SAP HANA.

* **Tratar o SAP HANA como uma fonte de dados relacional:** nesse caso, o Power BI trata o SAP HANA como uma fonte de dados relacional. Isso oferece maior flexibilidade. É necessário ter cuidado com essa abordagem para garantir que as medidas são agregadas conforme o esperado e para evitar problemas de desempenho.

A abordagem de conexão é determinada por uma opção de ferramenta global, que é configurada selecionando **arquivo > Opções e configurações** e, em seguida **opções > DirectQuery**, em seguida, selecionando a opção  **Tratar o SAP HANA como uma fonte relacional**, conforme mostrado na imagem a seguir. 

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01a.png)

A opção de tratar o SAP HANA como uma origem de dados relacional controla a abordagem usada para todos os *novos* relatórios usando DirectQuery no SAP HANA. Isso não tem efeito sobre as conexões existentes do SAP HANA no relatório atual, nem nas conexões em outros relatórios que estejam abertos. Portanto, se a opção estiver atualmente desmarcada, após a adição de uma nova conexão com o SAP HANA usando **Obter Dados**, essa conexão será feita considerando o SAP HANA como uma origem de dados multidimensional. No entanto, se um relatório diferente for aberto que também se conecta ao SAP HANA, esse relatório continuará se comportam de acordo com a opção que foi definida *no momento em que ele foi criado em*, o que significa que todos os relatórios se conectar ao SAP HANA que foram criado antes de fevereiro de 2018 continuarão a tratar o SAP HANA como uma fonte de dados relacional. 

As duas abordagens constituem um comportamento diferente e não é possível alternar um relatório existente de uma abordagem para o outro. 

Vamos ver cada uma dessas duas abordagens com mais detalhes, uma de cada vez.

## <a name="treat-sap-hana-as-a-multi-dimensional-source-default"></a>Tratar o SAP HANA como uma origem de dados multidimensional (padrão)

Todas as novas conexões com o SAP HANA usam esse método de conexão por padrão, tratando o SAP HANA como uma origem de dados multidimensional. Para tratar uma conexão com o SAP HANA como uma origem de dados relacional, você deve selecionar **Arquivo > Opções e configurações > Opções** e marcar a caixa em **DirectQuery > Tratar SAP HANA como uma origem de dados relacional**. Embora esse recurso esteja em **Versão prévia**, os relatórios criados usando a abordagem multidimensional *não poderão* ser publicados no serviço do Power BI, e fazer isso resultará em erros quando o relatório for aberto dentro do serviço do Power BI.  

Ao se conectar ao SAP HANA como uma origem multidimensional, as seguintes considerações se aplicam:

* No **Navegador de Obter Dados**, uma única exibição do SAP HANA pode ser selecionada. Não é possível selecionar atributos ou medidas individuais. Não há nenhuma consulta definida no momento da conexão, o que é diferente da importação de dados ou ao usar o DirectQuery e tratar o SAP HANA como uma origem de dados relacional. Isso também significa que não é possível usar uma consulta SQL do SAP HANA diretamente ao selecionar esse método de conexão.

* Todas as medidas, hierarquias e atributos do modo de exibição selecionado serão exibidos na lista de campos. 

* Como uma medida é usada em um visual, o SAP HANA será consultado para recuperar o valor da medida no nível de agregação necessário para o visual. Portanto, ao lidar com medidas não aditivas (contadores, proporções e assim por diante) todas as agregações serão executadas pelo SAP HANA e nenhuma outra agregação adicional será executada pelo Power BI. 

* Para garantir que os valores de agregação corretos sempre possam ser obtidos do SAP HANA, determinadas restrições deverão ser impostas. Por exemplo, não é possível adicionar colunas calculadas ou combinar dados de várias exibições do SAP HANA dentro do mesmo relatório. 

Tratar o SAP HANA como uma origem multidimensional não oferece uma flexibilidade maior do que a fornecida pela abordagem *relacional* alternativa, mas é mais simples e garante valores de agregação corretos ao lidar com medidas mais complexas do SAP HANA, além de geralmente resultar em um melhor desempenho. 

A lista **Campo** incluirá todas as medidas, atributos e hierarquias da exibição do SAP HANA. Observe os comportamentos a seguir que são aplicados ao usar esse método de conexão:

* Qualquer atributo que estiver incluído em pelo menos uma hierarquia ficará oculto por padrão. No entanto, eles podem ser vistos se necessário, selecionando **Exibir oculto** do menu de contexto na lista de campos. No mesmo menu de contexto, eles podem ficar visíveis, se isso for necessário.

* No SAP HANA, um atributo pode ser definido para usar outro atributo como seu rótulo. Por exemplo, **produto** (com valores de 1,2, 3 e assim por diante) poderia usar **ProductName** (com valores bicicleta, camisa, luvas e assim por diante) como seu rótulo. Nesse caso, um campo único **Produto** será mostrado na lista de campos, cujos valores serão os rótulos de Bicicleta,Camisa,Luvas e assim por diante, mas que será classificado por e com a exclusividade determinada pelos valores de chave 1,2,3. Uma coluna oculta **Product.Key** também é criada, permitindo o acesso aos valores de chave subjacentes se for necessário. 

Todas as variáveis definidas na exibição do SAP HANA subjacente serão mostradas no momento da conexão e os valores necessários poderão ser inseridos. Esses valores podem ser alterados posteriormente selecionando **editar consultas** na faixa de opções e então **gerenciar parâmetros** no menu suspenso exibido. 

As operações de modelagem permitidas são mais restritivas do que em geral, ao usar o DirectQuery, devido à necessidade de garantir que os dados de agregação corretos sempre possam ser obtidos do SAP HANA. No entanto, é possível fazer várias adições e alterações, incluindo a definição de medidas, renomeação e ocultação de campos e definição de formatos de exibição. Todas essas mudanças serão preservadas na atualização e as alterações não conflitantes feitas ao modo de exibição do SAP HANA serão aplicadas. 

### <a name="additional-modeling-restrictions"></a>Restrições de modelagem adicionais

As principais restrições de modelagem adicionais ao se conectar ao SAP HANA usando o DirectQuery (trate como uma fonte de dados multidimensional) são as seguintes: 

* **Não há suporte para colunas calculadas:** a capacidade de criar colunas calculadas fica desabilitada. Isso também significa que o Agrupamento e o Clustering, que criam colunas calculadas, não estão disponíveis.
* **Limitações adicionais para medidas:** há limitações adicionais impostas sobre as expressões DAX que podem ser usadas em medidas para refletir o nível de suporte oferecido pelo SAP HANA.
* **Não há suporte para definição de relações:** apenas uma única exibição pode ser consultada dentro de um relatório e, dessa forma, não há suporte para definição de relações.
* **Não há Modo de Exibição de Dados:** o **Modo de Exibição de Dados** normalmente exibe dados detalhados nas tabelas. Dada a natureza das fontes de OLAP como o SAP HANA, essa exibição não está disponível com o SAP HANA.
* **Detalhes de coluna e medidas são fixos:** a lista de colunas e medidas vista na lista de campos é fixa segundo a fonte subjacente e não pode ser modificada. Por exemplo, não é possível excluir uma coluna ou alterar seu tipo de dados (no entanto, é possível renomeá-la).
* **Limitações adicionais no DAX:** há limitações adicionais no DAX que podem ser usadas em definições de medida para refletir as limitações na fonte. Por exemplo, não é possível usar uma função de agregação em uma tabela.

### <a name="additional-visualization-restrictions"></a>Restrições de visualização adicionais

Há restrições nos elementos visuais ao se conectar ao SAP HANA usando o DirectQuery (trate como fonte de dados multidimensional): 
* **Não há agregação de colunas:** não é possível alterar a agregação para uma coluna em um visual; ela sempre é *Não Resumir*.

## <a name="treat-sap-hana-as-a-relational-source"></a>Tratar o SAP HANA como uma origem de dados relacional 

Ao decidir se conectar ao SAP HANA como uma origem de dados relacional, outras flexibilidades adicionais ficam disponíveis. Por exemplo, você pode criar colunas calculadas, incluir dados de vários modos de exibição do SAP HANA e criar relações entre as tabelas resultantes. No entanto, ao usar o SAP HANA dessa maneira, é importante entender determinados aspectos de como as conexões são tratadas, para garantir o seguinte: 

* os resultados correspondam ao esperado quando o modo de exibição do SAP HANA contiver medidas não aditivas (por exemplo, contagens distintas ou médias, em vez de somas simples).
* as consultas resultantes sejam eficientes

É útil começar esclarecendo o comportamento de uma fonte relacional, como um SQL Server, quando a consulta definida em **Obter Dados** ou no **Editor de Consultas** executar uma agregação. No exemplo a seguir, uma consulta definida no **Editor de Consultas** retorna o preço médio segundo o *ProductID*.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Se os dados estiverem sendo importados para o Power BI (em vez de usar o DirectQuery), aconteceria o seguinte:

* Os dados são importados no nível de agregação definido pela consulta criada no **Editor de Consultas**. Por exemplo, preço médio por produto. Isso resulta em uma tabela com duas colunas, *ProductID* e *AveragePrice*, que podem ser usadas em visuais.
* Em um visual, qualquer agregação subsequente (como *Sum*, *Average*, *Min*, entre outras) é executada nos dados importados. Por exemplo, incluir *AveragePrice* em um visual usará a agregação *Sum* por padrão e retornará a soma de *AveragePrice* para cada *ProductID* – que nesse caso de exemplo seria 13,67. O mesmo se aplica a qualquer função de agregação alternativa (como *Min*, *Average* etc) usada no visual. Por exemplo, *médio* dos *AveragePrice* retorna a média de 6,66, 4 e 3, que é igual a 4,56, e não a média dos *preço* nos registros de seis subjacente tabela, que é 5,17.
  
Se o **DirectQuery** (nessa mesma fonte relacional) estiver sendo usado em vez da Importação, a mesma semântica se aplica e os resultados seriam exatamente os mesmos:  

* Considerando a mesma consulta, logicamente os mesmos dados seriam apresentados para a camada de relatório, embora os dados não tenham sido de fato importados.

* Em um visual, qualquer agregação subsequente (*Sum*, *Average*, *Min*, entre outras) é executada mais uma vez na tabela lógica da consulta. E mais uma vez, um visual contendo *Average* de *AveragePrice* retornará o mesmo valor de 4,56.
  
Agora vamos considerar SAP HANA, quando a conexão é tratada como uma fonte relacional. O Power BI pode trabalhar com *Exibições Analíticas* e *Exibições de Cálculo* no SAP HANA, que podem conter medidas. Ainda hoje a abordagem do SAP HANA segue os mesmos princípios descritos anteriormente nesta seção: a consulta definida em **Obter Dados** ou no **Editor de Consultas** determinará os dados disponíveis e qualquer agregação subsequente em um visual será feita nos dados e o mesmo se aplica à Importação e ao DirectQuery.  
No entanto, devido à natureza do SAP HANA, a consulta definida na caixa de diálogo inicial **Obter Dados** ou **Editor de Consultas** sempre será uma consulta de agregação e geralmente incluirá medidas em que a agregação real que será usada será definida pela exibição do SAP HANA.

O equivalente do exemplo do SQL Server acima é que há uma exibição do SAP HANA contendo *ID*, *ProductID*, *DepotID* e medidas incluindo *AveragePrice*, definidas no modo de exibição como *Média do Preço*.  
    
Se estiver na **obter dados** experiência, as seleções feitas eram de **ProductID** e o **AveragePrice** medir, que define uma consulta no modo de exibição, solicitando que agregar dados (no exemplo anterior, para manter a simplicidade pseudo-SQL que é usado não coincide com a sintaxe exata do SAP HANA SQL). Em seguida, agregações adicionais definidas em um visual agregam ainda mais os resultados de tal consulta. Novamente, conforme descrito acima para o SQL Server, isso se aplica tanto ao caso da Importação quanto ao DirectQuery. No caso do DirectQuery, a consulta do **obter dados** ou **Editor de consultas** será usado em uma Subseleção dentro de uma única consulta enviada ao SAP HANA e, portanto, não é, na verdade, caso em que todos os dados seriam lidos antes Para mais de agregação.  

Todas essas considerações e comportamentos exigem as seguintes considerações importantes ao usar o DirectQuery no SAP HANA:  

* É necessário prestar atenção a qualquer agregação adicional executada nos visuais, sempre que a medida no SAP HANA for não aditiva (por exemplo, não for um simples *Sum*, *Min* ou *Max*).

* Em **Obter Dados** ou no **Editor de Consultas**, somente as colunas obrigatórias devem ser incluídas para recuperar os dados necessários, refletindo o fato de que o resultado será uma consulta, que deverá ser uma consulta razoável que possa ser enviada ao SAP HANA. Por exemplo, se dezenas de colunas tiverem sido selecionadas, com a ideia de que eles podem ser necessárias em visuais posteriores, em seguida, até mesmo para o DirectQuery um visual simples significará a consulta de agregação usada na Subseleção conterá essas dezenas de colunas, que serão geralmente desempenho insatisfatório.
  
Vejamos um exemplo. No exemplo a seguir, selecionar cinco colunas (**CalendarQuarter**, **Color**, **LastName**, **ProductLine**, **SalesOrderNumber**) na caixa de diálogo **Obter Dados**, junto com a medida *OrderQuantity*, significa que, mais tarde, a criação de um visual simples contendo Min OrderQuantity resultará na seguinte consulta SQL ao SAP HANA. O sombreado é a subseleção, contendo a consulta de **Obter Dados** / **Editor de Consultas**. Se essa Subseleção levar a um resultado de alta cardinalidade, o desempenho resultando do HANA SAP provavelmente será ruim.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

   
Por causa deste comportamento, recomendamos que os itens selecionados em **Obter Dados** ou no **Editor de Consultas** sejam limitados aos itens que são necessários, ainda assim resultando em uma consulta razoável ao SAP HANA.  

## <a name="best-practices"></a>Práticas recomendadas 

Para ambas as abordagens para se conectar ao SAP HANA, as recomendações para usar o DirectQuery também se aplicam ao SAP HANA, especialmente as relacionadas a garantir o bom desempenho. Essas recomendações estão descritas detalhadamente no artigo [Usando o DirectQuery no Power BI](desktop-directquery-about.md).
   
## <a name="limitations"></a>Limitações

A lista a seguir descreve todos os recursos do SAP HANA que não têm suporte completo ou recursos que têm comportamento diferente ao usar o Power BI. 

* **Hierarquias de pai/filho** – hierarquias pai/filho não estarão visíveis no Power BI.
Isso ocorre porque o Power BI acessa o SAP HANA usando a interface do SQL e as hierarquias de pai/filho não podem ser totalmente acessadas por meio do SQL.
* **Outros metadados de hierarquia** – a estrutura básica das hierarquias é exibida no Power BI; no entanto, alguns metadados de hierarquia (como controlar o comportamento de hierarquias desbalanceadas) não terão efeito.
Novamente, isso é devido a limitações impostas pela interface do SQL.
* **Conexão usando SSL** – você pode se conectar usando a importação e multidimensionais com SSL, comprar não pode se conectar a instâncias do SAP HANA configuradas para usar SSL para o conector relacional.
* **Suporte a modos de exibição de Atributo** – o Power BI pode se conectar aos modos de exibição Analítico e de Cálculo, mas não pode se conectar diretamente aos modos de exibição de Atributo.
* **Suporte para objetos de catálogo** – o Power BI não pode se conectar aos objetos de catálogo.
* **Alterar para Variáveis após publicar** – você não pode alterar os valores das variáveis do SAP HANA diretamente no serviço do Power BI, após o relatório ser publicado. 
 
## <a name="known-issues"></a>Problemas conhecidos 
A lista a seguir descreve todos os problemas conhecidos ao se conectar ao SAP HANA (DirectQuery) usando o Power BI. 

* **Problema do SAP HANA ao consultar Contadores e outras medidas** – dados incorretos são retornados do SAP HANA se estiver conectando a uma Exibição Analítica e uma medida de Contador, bem como algumas outras medidas de proporção, estiverem incluídas no mesmo visual. Isso é abordado pela observação 2128928 do SAP (resultados inesperados ao consultar uma coluna calculada e um contador). A medida de proporção estará incorreta nesse caso. 

* **Várias colunas do Power BI de coluna única do SAP HANA** – para algumas exibições de cálculo em que uma coluna do SAP HANA é usada em mais de uma hierarquia, o SAP HANA expõe isso como dois atributos separados. Isso resulta em duas colunas que estão sendo criadas no Power BI.  No entanto, essas colunas estão ocultos por padrão e todas as consultas que envolvem hierarquias ou as colunas diretamente comportam-se corretamente. 
 
## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o DirectQuery, confira os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway de dados local](service-gateway-onprem.md)

