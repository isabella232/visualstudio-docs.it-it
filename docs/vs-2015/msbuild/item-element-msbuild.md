---
title: Elemento Item (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50bcae08190d052d02ec2cf468396692163a272d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527250"
---
# <a name="item-element-msbuild"></a>Elemento Item (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elemento Item (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/item-element-msbuild).  
  
  
Contiene un elemento definito dall'utente e i relativi metadati. Ogni elemento usato in un progetto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] deve essere specificato come elemento figlio di un elemento `ItemGroup`.  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Include`|Attributo obbligatorio.<br /><br /> Il file o carattere jolly da includere nell'elenco di elementi.|  
|`Exclude`|Attributo facoltativo.<br /><br /> Il file o carattere jolly da escludere dall'elenco di elementi.|  
|`Condition`|Attributo facoltativo.<br /><br /> La condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  
|`Remove`|Attributo facoltativo.<br /><br /> Il file o carattere jolly da eliminare dall'elenco di elementi.<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|  
|`KeepMetadata`|Attributo facoltativo.<br /><br /> I metadati per gli elementi di origine da aggiungere agli elementi di destinazione. Solo i metadati i cui nomi vengono specificati nell'elenco delimitato da punto e virgola vengono trasferiti da un elemento di origine a un elemento di destinazione. Per altre informazioni, vedere [Items](../msbuild/msbuild-items.md) (Elementi).<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|  
|`RemoveMetadata`|Attributo facoltativo.<br /><br /> I metadati per gli elementi di origine da non trasferire agli elementi di destinazione. Tutti i metadati vengono trasferiti da un elemento di origine a un elemento di destinazione, ad eccezione dei metadati i cui nomi sono contenuti nell'elenco di nomi separati da punto e virgola. Per altre informazioni, vedere [Items](../msbuild/msbuild-items.md) (Elementi).<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|  
|`KeepDuplicates`|Attributo facoltativo.<br /><br /> Specifica se un elemento deve essere aggiunto al gruppo di destinazione se è un duplicato esatto di un elemento esistente. Se l'elemento di origine e destinazione hanno lo stesso valore `Include`, ma metadati diversi, l'elemento viene aggiunto anche se `KeepDuplicates` è impostato su `false`. Per altre informazioni, vedere [Items](../msbuild/msbuild-items.md) (Elementi).<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Chiave dei metadati di elemento definita dall'utente che contiene il valore dei metadati dell'elemento. Possono esistere zero o più elementi `ItemMetadata` in un elemento.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento di raggruppamento per elementi.|  
  
## <a name="remarks"></a>Note  
 Gli elementi `Item` definiscono gli input nel sistema di compilazione e vengono raggruppati in raccolte di elementi in base ai relativi nomi definiti dall'utente. Queste raccolte di elementi possono essere usate come parametri per le [attività](../msbuild/msbuild-tasks.md), che a loro volta usano i singoli elementi nelle raccolte per eseguire i passaggi del processo di compilazione. Per altre informazioni, vedere [Items](../msbuild/msbuild-items.md) (Elementi).  
  
 L'uso della notazione `@(`*myType*`)` consente di espandere una raccolta di elementi di tipo *myType* in un elenco di stringhe delimitato da punto e virgola e di passarla a un parametro. Se il parametro è di tipo `string`, il valore del parametro è l'elenco di elementi, separati da punti e virgola. Se il parametro è una matrice di stringhe (`string[]`), ogni elemento viene inserito nella matrice in base alla posizione dei punti e virgola. Se il parametro dell'attività è di tipo <xref:Microsoft.Build.Framework.ITaskItem>`[]`, il valore è il contenuto della raccolta di elementi con eventuali metadati associati. Per delimitare ciascun elemento usando un carattere diverso da un punto e virgola, usare la sintassi `@(`*myType*`, '`*separatore*`')`.  
  
 Il motore [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] può valutare caratteri jolly come `*` e `?`, oltre ai caratteri jolly ricorsivi come `/**/*.cs`. Per altre informazioni, vedere [Items](../msbuild/msbuild-items.md) (Elementi).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come dichiarare due elementi di tipo `CSFile`. Il secondo elemento dichiarato contiene i metadati con `MyMetadata` impostato su `HelloWorld`.  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi](../msbuild/msbuild-items.md)   
 [Proprietà di MSBuild](msbuild-properties1.md)   
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)



