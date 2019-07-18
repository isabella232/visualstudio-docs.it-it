---
title: 'Procedura: Visualizzare un elenco di elementi separati da virgole | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 93451d6d49082621df48c734de951e6a4bc7e281
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156639"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Procedura: visualizzare un elenco di elementi separati da virgole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si usano gli elementi elencati in [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]), è talvolta utile visualizzare il contenuto di tali elenchi di elementi in un modo facilmente leggibile. In alternativa, si potrebbe usare un attività che accetta un elenco di elementi separati da una stringa di separazione speciale. In entrambi i casi, è possibile specificare una stringa di separazione per un elenco di elementi.  
  
## <a name="separating-items-in-a-list-with-commas"></a>Separazione di elementi in un elenco con virgole  
 Per impostazione predefinita, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] usa i punti e virgola per separare gli elementi in un elenco. Si consideri ad esempio un elemento `Message` con il valore seguente:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Quando l'elenco di elementi `@(TXTFile)` contiene gli elementi App1.txt, App2.txt e App3.txt, il messaggio è:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Se si vuole modificare il comportamento predefinito, è possibile specificare un separatore personalizzato. La sintassi per specificare un separatore per un elenco di elementi è:  
  
 `@(ItemListName, '<separator>')`  
  
 Il separatore può essere un singolo carattere o una stringa e deve essere racchiuso tra virgolette singole.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Per inserire una virgola e uno spazio tra gli elementi  
  
- Usare una notazione simile alla seguente:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Esempio  
 In questo esempio, l'attività [Exec](../msbuild/exec-task.md) esegue lo strumento findstr per trovare le stringhe di testo specificate nel file Phrases.txt. Nel comando findstr le stringhe di ricerca letterali sono indicate dall'opzione **/c:** , pertanto il separatore di elementi `/c:` viene inserito tra gli elementi nell'elenco di elementi `@(Phrase)`.  
  
 Per questo esempio, la riga di comando equivalente è:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Elementi](../msbuild/msbuild-items.md)
