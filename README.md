# Apresentação:

Relatório referente a avaliação do modelo **Prithvi WxC**, uma iniciativa da **NASA** em parceria com a **IBM _Research_** visando gerar um modelo de _deep learning_ **fundacional** voltado para tarefas meteorológicas relacionadas com tempo e clima.

## Material de Base:

A base do relatório é o [artigo original do modelo](https://arxiv.org/pdf/2409.13598) , sendo aqui complementado algumas informações relacionadas a área da meteorologia, tendo como material de apoio:

* [**Documentação do Merra-2**](https://doi.org/10.1175/JCLI-D-16-0758.1): NASA.
* **Probabilistic Machine Learning: An Introduction** de _Kevin P. Murphy_;
* **Sensoriamento Remoto do Ambiente** de _John R. Jensen_.

# Modelo:

**Prithvi WxC** é um modelo **fundacional** de grande escala desenvolvido para aplicações meteorológicas e climáticas. Com uma arquitetura **_based-Transformers_ (encoder-decoder)**.  O modelo incorpora conceitos modernos para capturar eficazmente as dependências regionais e globais dos dados atmosféricos, utilizando 160 variáveis do conjunto de dados **MERRA-2** e treinando com $20$ anos de dados, seguindo a metodologia da climatologia do _ERA-Interim_ (Janousek, 2011).

	Nota: O ERA-Interim foi um conjunto de dados de reanálise desenvolvido pelo Centro Europeu de Previsão do Tempo de Médio Prazo (ECMWF). Ele fornecia uma descrição abrangente das condições atmosféricas globais, sendo utilizado até ser substituído pelo ERA5. A metodologia da climatologia do ERA-Interim, conforme mencionada em Janousek (2011), envolvia o uso de técnicas avançadas de assimilação de dados para combinar observações com modelos atmosféricos, produzindo uma representação consistente e detalhada do clima em diferentes períodos, o que permitia estudos sobre variabilidade e tendências climáticas.

O modelo é inspirado no [ViT (Visual Transformers)](https://arxiv.org/pdf/2010.11929), e busca ser flexível escalável e flexível, semelhante ao **ViT**, porém permitindo lidar com grandes contagens de _tokens_ e diferentes contextos espaciais, diferente do **ViT**, que possuí limitações nesses contexto. Essa flexibilidade é crucial para modelar fenômenos climáticos em resoluções finas.

A validação do **Prithvi WxC** se estende de avaliações de _zero-shot_ para reconstrução e previsão a tarefas posteriores, de modo que ele é treinado com um objetivo misto que combina os paradigmas de **_masked reconstruction_** com **_forecasting_**., Segundo o artigo original, o modelo foi testado nas seguintes tarefas:

* Previsão autoregressiva em cadeia (Série Temporal);
	* Previsão contínua do estado atmosférico, utilizando as próprias previsões do modelo como entrada para futuras etapas. 
* _Downscaling_;
	* Refinamento de previsões climáticas de uma resolução grosseira para uma resolução mais fina, capturando detalhes regionais específicos.
* Parametrização de fluxo de ondas de gravidade; e
	* Representação dos efeitos das **ondas gravitacionais** no clima, que afetam o transporte de energia e momento na atmosfera.
* Estimativa de eventos extremos.
	* Estimativa e previsão de eventos climáticos extremos, como tempestades severas e ondas de calor.
# Dados:

## Merra-2:

O **MERRA-2 (_Modern-Era Retrospective analysis for Research and Applications_, Version 2)** é um o que os meteorologistas chamam de **dados de reanálise**, que podem ser simplificados como uma junção **estruturada** de dados de várias fontes diferentes, de modo a combinar medições observacionais, como de satélites, balões meteorológicos e estações de superfície, com modelos de previsão do tempo, resultando em um conjunto de dados consistente e detalhado, adequado para análises climáticas e meteorológicas.

O MERRA-2, em particular, foi introduzido devido aos avanços no sistema de assimilação que permitem a assimilação de **radiâncias hiperespectrais modernas** e **observações de micro-ondas**, juntamente com conjuntos de dados de **Ocultação por Rádio GPS**. Também utiliza observações do perfil de ozônio da NASA, que começaram no final de 2004.

# Conclusão:

Apesar de mencionar abordagens que mesclam _deep learning_ e modelos fisico-matemáticos, a estratégia aqui, adotada pela **NASA** em junção a **IBM _Research_**, foi focar em um modelo de _deep learning_ apenas.

O não fornece uma comparação direta com modelos físico-matemáticos tradicionais ou métodos numéricos de previsão do tempo, de modo que fornece apenas informações sobre o desempenho do modelo em questão, em relação às linhas de base de interpolação, com o foco em mostrar as vantagens da abordagem baseada em IA na redução de tarefas.
