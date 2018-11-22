## <a name="limitations"></a>Limitações

Veja a seguir uma lista com as limitações atuais da Segurança em Nível de Linha nos modelos de nuvem.

* Se você definiu funções e regras anteriormente no serviço do Power BI, deverá criá-las novamente no Power BI Desktop.

* Você pode definir a RLS somente nos conjuntos de dados criados com o Power BI Desktop. Se desejar habilitar a RLS para conjuntos de dados criados com o Excel, deverá primeiro converter os arquivos em arquivos PBIX (Power BI Desktop). [Saiba mais](../desktop-import-excel-workbooks.md)

* Somente há suporte para conexões ETL e DirectQuery. Conexões dinâmicas do Analysis Services são tratadas no modelo local.

* No momento, não há suporte para a P e R e Cortana com RLS. Você não verá a caixa de entrada da P e R para os dashboards se todos os modelos tiverem a RLS configurada. Isso está em nossos planos, mas ainda não há um cronograma disponível.

## <a name="known-issues"></a>Problemas conhecidos

Há um problema conhecido em que você obterá uma mensagem de erro se tentar publicar um relatório publicado anteriormente no Power BI Desktop. O cenário é descrito a seguir.

1. Sara tem um conjunto de dados que foi publicado no serviço do Power BI e ela configurou a RLS.

1. Sara atualiza o relatório no Power BI Desktop e o publica novamente.

1. Sara recebe um erro.

**Solução alternativa:** publique novamente o arquivo do Power BI Desktop no serviço do Power BI até que esse problema seja resolvido. Você pode fazer isso selecionando **Obter Dados** > **Arquivos**.
