---
title: UriTemplate and UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 66463248f66457aa61ceea22afd003f7b93717e1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198404"
---
# <a name="uritemplate-and-uritemplatetable"></a>UriTemplate and UriTemplateTable
Os desenvolvedores da Web exigem a capacidade para descrever a forma e o layout dos URIs que seus serviços respondem a. Windows Communication Foundation (WCF) adicionadas duas novas classes para dar aos desenvolvedores controle sobre seus URIs. <xref:System.UriTemplate> e <xref:System.UriTemplateTable> formam a base do mecanismo de expedição baseada em URI no WCF. Essas classes também podem ser usadas em seu próprios, permitindo que os desenvolvedores tirem proveito de modelos e o URI de mecanismo de mapeamento sem implementar um serviço WCF.  
  
## <a name="templates"></a>Modelos  
 Um modelo é uma maneira de descrever um conjunto de URIs relativos. O conjunto de modelos URI na tabela a seguir mostra como um sistema que recupera vários tipos de informações meteorológicas pode ser definido.  
  
|Dados|Modelo|  
|----------|--------------|  
|Previsão nacional|clima/nacional|  
|Previsão do estado|clima / {state}|  
|Previsão de cidade|clima / {state} / {cidade}|  
|Previsão de atividade|clima / {state} / {cidade} / {atividade}|  
  
 Esta tabela descreve um conjunto de URIs estruturalmente semelhantes. Cada entrada é um modelo de URI. Os segmentos entre chaves descrevem variáveis. Os segmentos não entre chaves descrevem cadeias de caracteres literais. As classes de modelo WCF permitir que os desenvolvedores utilizam um URI de entrada, por exemplo, "/ clima/wa/seattle/circulando" e fazer sua correspondência para um modelo que descreve, "/weather/ {estado} / {cidade} / {atividade}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> é uma classe que encapsula um modelo de URI. O construtor aceita um parâmetro de cadeia de caracteres que define o modelo. Essa cadeia de caracteres contém o modelo no formato descrito na próxima seção. O <xref:System.UriTemplate> classe fornece métodos que permitem que você correspondem a um URI de entrada para um modelo, gerar um URI de um modelo, recuperar uma coleção de nomes variáveis usados no modelo, determinar se dois modelos são equivalentes e retornam o modelo cadeia de caracteres.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> usa um endereço básico e um candidato URI e tenta corresponder o URI para o modelo. Se a correspondência for bem-sucedida, um <xref:System.UriTemplateMatch> instância será retornada. O <xref:System.UriTemplateMatch> objeto contém um URI de base, o URI, uma coleção de nome/valor de parâmetros de consulta, uma matriz dos segmentos de caminho relativa, uma coleção de nome/valor das variáveis que foram correspondidas, candidato a <xref:System.UriTemplate> usada para executar a correspondência de instância , uma cadeia de caracteres que contém qualquer parte não correspondentes do candidato URI (usado quando o modelo tem um caractere curinga) e um objeto que está associado com o modelo.  
  
> [!NOTE]
>  O <xref:System.UriTemplate> classe ignora o número da porta e o esquema durante a correspondência de um URI candidato para um modelo.  
  
 Há dois métodos que permitem que você gerar um URI de um modelo <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> e <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>. <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> usa um endereço base e uma coleção de nome/valor de parâmetros. Esses parâmetros são substituídos por variáveis quando o modelo está associado. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> usa os pares nome/valor e substitui-los da esquerda para a direita.  
  
 <xref:System.UriTemplate.ToString> Retorna a cadeia de caracteres de modelo.  
  
 O <xref:System.UriTemplate.PathSegmentVariableNames%2A> propriedade contém uma coleção dos nomes das variáveis usadas dentro de segmentos de caminho na cadeia de caracteres de modelo.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> leva um <xref:System.UriTemplate> como um parâmetro e retorna um valor booliano que especifica se os dois modelos são equivalentes. Para obter mais informações, consulte a seção de equivalência de modelo mais adiante neste tópico.  
  
 <xref:System.UriTemplate> foi projetado para trabalhar com qualquer esquema URI que esteja de acordo com a gramática do URI do HTTP. A seguir estão exemplos de esquemas URI com suporte.  
  
- http://  
  
- https://  
  
- net.tcp://  
  
- NET.pipe://  
  
- sb://  
  
 Esquemas como file:// e urn: / / não está em conformidade com a gramática do URI do HTTP e causar resultados imprevisíveis quando usada com modelos URI.  
  
### <a name="template-string-syntax"></a>Sintaxe de cadeia de caracteres de modelo  
 Um modelo tem três partes: um caminho, uma consulta opcional e um fragmento opcional. Para obter um exemplo, consulte o modelo a seguir:  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 O caminho consiste em "/weather/ {estado} / {cidade}", a consulta consiste em"? previsão = {comprimento}, e o fragmento consiste em"#frag1".  
  
 À esquerda e à direita barras "/" são opcionais na expressão de caminho. Expressões de consulta e de fragmento podem ser totalmente omitidas. Um caminho consiste em uma série de segmentos delimitados por '/', cada segmento pode ter um valor literal, um nome de variável (escrito em {entre chaves}) ou um caractere curinga (escrito como\*'). No modelo anterior a "\weather\ segmento é um literal"{city}"e o valor de"{state}"são variáveis. Variáveis têm seu nome do conteúdo de suas chaves e posteriormente podem ser substituídos por um valor concreto para criar uma *fechado URI*. O caractere curinga é opcional, mas só pode aparecer no final do URI, onde ele corresponde logicamente "o restante do caminho".  
  
 A expressão de consulta, se presente, especifica uma série de pares nome/valor não ordenada delimitadas por '&'. Elementos da expressão de consulta podem ser literais pares (x = 2) ou um par de variáveis (x = {var}). Somente o lado direito da consulta pode ter uma expressão variável. ({someName} = {Algumvalor} não é permitido. Não emparelhado valores (? x) não são permitidos. Não há nenhuma diferença entre uma expressão de consulta vazia e uma expressão de consulta consiste em apenas uma única '?' (ambos dizer "qualquer consulta").  
  
 A expressão de fragmento pode consistir em um valor literal, não há variáveis são permitidas.  
  
 Todos os nomes de variável de modelo dentro de uma cadeia de caracteres de modelo devem ser exclusivos. Nomes de variável de modelo diferenciam maiusculas de minúsculas.  
  
 Exemplos de cadeias de caracteres de modelo válido:  
  
- ""  
  
- "/ sapato"  
  
- "/shoe/\*"  
  
- "{calçado} / barco"  
  
- "{calçado} / {barco} /bed/ {quilt}"  
  
- "calçado / {barco}"  
  
- "calçado / {barco} /\*"  
  
- "calçado/barco? x = 2"  
  
- "calçado / {barco}? x = {cama}"  
  
- "calçado / {barco}? x = {cama} & y = faixa"  
  
- "?x={shoe}"  
  
- "calçados? x = 3 & y = {var}  
  
 Exemplos de cadeias de caracteres de modelo inválido:  
  
- "{calçado} / {CALÇADO} / x = 2" – duplicar os nomes de variáveis.  
  
- "{calçado} /boat/? cama = {calçado}" – duplicar os nomes de variáveis.  
  
- "? x = x & 2 = 3" – pares nome-valor dentro de uma cadeia de caracteres de consulta devem ser exclusivos, mesmo se eles são literais.  
  
- "? x = 2 &" – cadeia de caracteres de consulta está malformada.  
  
- "? 2 & x = {calçado}" – cadeia de caracteres de consulta deve ser pares nome/valor.  
  
- "? y = 2 & & X = 3" – cadeia de caracteres de consulta deve ser pares de valor de nome, nomes não podem começar com '&'.  
  
### <a name="compound-path-segments"></a>Composto de segmentos de caminho  
 Segmentos de caminho composto permitem que um único segmento de caminho URI conter várias variáveis, bem como variáveis combinadas com literais. A seguir estão exemplos de segmentos de caminho composto válido.  
  
- /filename.{ext}/  
  
- /{filename}.jpg/  
  
- /{filename}.{ext}/  
  
- / {a}. {b}someLiteral{c}({d}) /  
  
 A seguir estão exemplos de segmentos de caminho inválido.  
  
- /{} -Variáveis devem ser nomeadas.  
  
- / {calçado} {barco} - variáveis devem ser separadas por um literal.  
  
### <a name="matching-and-compound-path-segments"></a>Segmentos de caminho correspondentes e compostas  
 Segmentos de caminho composto permitem que você defina um UriTemplate que tem diversas variáveis dentro de um único segmento de caminho. Por exemplo, na seguinte cadeia de caracteres de modelo: "endereços / {state}. {Cidade} "duas variáveis (estado e cidade) são definidas dentro do mesmo segmento. Este modelo corresponderia a uma URL como `http://example.com/Washington.Redmond` , mas também serão compatíveis com uma URL como `http://example.com/Washington.Redmond.Microsoft`. No último caso, a variável de estado conterá "Washington" e a variável de cidade irá conter "Redmond.Microsoft". Nesse caso, qualquer texto (exceto '/') corresponderá a variável {cidade}. Se você quiser um modelo que não corresponderá o texto "extra", coloca a variável em um segmento de modelo separado, por exemplo: "endereços / {state} / {cidade}.  
  
### <a name="named-wildcard-segments"></a>Segmentos nomeados curinga  
 Um segmento curinga nomeado é qualquer segmento de caminho variável cujo nome de variável começa com o caractere curinga '\*'. A seguinte cadeia de caracteres de modelo contém um segmento curinga nomeado chamado "sapato".  
  
```  
"literal/{*shoe}"  
```  
  
 Segmentos de curinga devem seguir as regras a seguir:  
  
- Pode haver no máximo um segmento de curinga nomeada para cada cadeia de caracteres de modelo.  
  
- Um segmento curinga nomeados deve aparecer no segmento mais à direita no caminho.  
  
- Um segmento curinga nomeado não pode coexistir com um segmento curinga anônimo dentro a mesma cadeia de caracteres de modelo.  
  
- O nome de um segmento curinga nomeada deve ser exclusivo.  
  
- Chamado curinga segmentos não podem ter valores padrão.  
  
- Segmentos de curinga nomeado não podem terminar com "/".  
  
### <a name="default-variable-values"></a>Valores de variáveis padrão  
 Os valores de variáveis padrão permitem que você especifique valores padrão para variáveis dentro de um modelo. Variáveis de padrão podem ser especificadas com as chaves que declarar a variável ou como uma coleção passada para o construtor UriTemplate. O modelo a seguir mostra duas maneiras para especificar um <xref:System.UriTemplate> com variáveis com valores padrão.  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Este modelo declara uma variável nomeada `a` com um valor padrão de `1` e uma variável chamada `b` com um valor padrão de `5`.  
  
> [!NOTE]
>  Somente as variáveis de segmento de caminho têm permissão para ter valores padrão. Variáveis de cadeia de caracteres de consulta, as variáveis de segmento composta e variáveis nomeadas curinga não são permitidas para ter valores padrão.  
  
 O código a seguir mostra como os valores de variáveis padrão são tratados durante a correspondência de um URI candidato.  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> Um URI, como `http://localhost:8000///` não coincide com o modelo listado no código anterior, porém um URI, como `http://localhost:8000/` faz.  
  
 O código a seguir mostra como os valores de variáveis padrão são tratados durante a criação de um URI com um modelo.  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
Quando uma variável recebe um valor padrão de `null` há algumas restrições adicionais. Uma variável pode ter um valor padrão de `null` se a variável está contida no segmento mais à direita da cadeia de caracteres de modelo ou se todos os segmentos à direita do segmento têm valores padrão de `null`. A seguir é cadeias de caracteres de modelo válido com valores padrão de `null`:  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 A seguir é cadeias de caracteres de modelo inválido com valores padrão de `null`:  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a>Correspondência e os valores padrão  
 Ao fazer a correspondência de um candidato URI com um modelo que tem valores padrão, os valores padrão são colocados no <xref:System.UriTemplateMatch.BoundVariables%2A> coleção se os valores não são especificados em que o URI candidato.  
  
### <a name="template-equivalence"></a>Equivalência de modelo  
 Dois modelos são considerados *estruturalmente equivalente* quando todos os literais dos modelos correspondem e têm variáveis nos mesmos segmentos. Por exemplo, os seguintes modelos são estruturalmente equivalentes:  
  
- /a/ {var1} / b b / {var2}? x = 1 & y = 2  
  
- a/{x}/b%20b/{var1}?y=2 & x = 1  
  
- a/{y}/B%20B/{z}/?y=2&x=1  
  
 Algumas coisas a observar:  
  
- Se um modelo contém barras à esquerda, somente o primeiro deles será ignorado.  
  
- Ao comparar cadeias de caracteres de modelo para equivalência estrutural, caso é ignorado para nomes de variáveis e segmentos de caminho, cadeias de caracteres de consulta diferenciam maiusculas de minúsculas.  
  
- Cadeias de caracteres de consulta são ordenadas.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 O <xref:System.UriTemplateTable> classe representa uma tabela associativa de <xref:System.UriTemplate> objetos associados a um objeto do desenvolvedor do escolhendo. Um <xref:System.UriTemplateTable> deve conter pelo menos um <xref:System.UriTemplate> antes de chamar <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. O conteúdo de um <xref:System.UriTemplateTable> pode ser alterada até <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado. A validação é executada quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado. O tipo de validação executada depende do valor de `allowMultiple` parâmetro para <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.  
  
 Quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado passando `false`, o <xref:System.UriTemplateTable> verificações para garantir que não existem modelos na tabela. Se ele encontrar quaisquer modelos estruturalmente equivalentes, ele gerará uma exceção. Isso é usado em conjunto com <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> quando você deseja garantir que apenas um modelo corresponde a um URI de entrada.  
  
 Quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado passando `true`, <xref:System.UriTemplateTable> permite que vários modelos estruturalmente equivalente a ser contido dentro de um <xref:System.UriTemplateTable>.  
  
 Se um conjunto de <xref:System.UriTemplate> objetos adicionados a um <xref:System.UriTemplateTable> contêm cadeias de caracteres de consulta não deve ser ambíguas. Cadeias de caracteres de consulta idênticos são permitidas.  
  
> [!NOTE]
>  Enquanto o <xref:System.UriTemplateTable> permite que a base de dados de endereços que esquemas de uso diferente de HTTP, o esquema e número da porta são ignorados durante a correspondência de URIs candidatos aos modelos.  
  
### <a name="query-string-ambiguity"></a>Ambiguidade da cadeia de caracteres de consulta  
 Modelos que compartilham um caminho equivalente contêm cadeias de caracteres de consulta ambígua se não houver um URI que corresponde a mais de um modelo.  
  
 Os seguintes conjuntos de cadeias de caracteres de consulta são não ambíguos em si mesmos:  
  
- ?x=1  
  
- ? x = 2  
  
- ?x=3  
  
- ? x = 1 & y = {var}  
  
- ? x = 2 e z = {var}  
  
- ?x=3  
  
- ?x=1  
  
- ?  
  
- ? x={var}  
  
- ?  
  
- ?m=get&c=rss  
  
- ? m = put & c = rss  
  
- ?m=get&c=atom  
  
- ? m = put & c = atom  
  
 Os seguintes conjuntos de modelos de cadeia de caracteres de consulta são ambíguos em si mesmos:  
  
- ?x=1  
  
- ?x={var}  
  
 "x = 1"-corresponde a ambos os modelos.  
  
- ?x=1  
  
- ? y = 2  
  
 "x = 1 & y = 2" corresponde a ambos os modelos. Isso ocorre porque uma cadeia de caracteres de consulta pode conter mais variáveis de cadeia de caracteres de consulta e em seguida, o modelo que ela corresponde.  
  
- ?x=1  
  
- ? x = 1 & y = {var}  
  
 "x = 1 & y = 3" corresponde a ambos os modelos.  
  
- ? x = 3 & y = 4  
  
- ?x=3&z=5  
  
> [!NOTE]
> Os caracteres á e Á são considerados diferentes caracteres quando eles são exibidos como parte de um caminho de URI ou <xref:System.UriTemplate> literal do segmento de caminho (mas os caracteres a e A são considerados para ser o mesmo). Os caracteres á e Á são considerados os mesmos caracteres quando eles são exibidos como parte de um <xref:System.UriTemplate> {variableName} ou uma cadeia de caracteres de consulta (e a e também são considerados para ser os mesmos caracteres).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [Modelo de objeto de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [Tabela de UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [Dispatcher de Tabela de UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
