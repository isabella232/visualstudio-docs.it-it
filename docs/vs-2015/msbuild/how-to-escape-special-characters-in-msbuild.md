---
title: 'Procedura: Usare caratteri di escape per caratteri speciali in MSBuild | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94fc8d858e2db9bd1e00bb8770cf52672a900ab0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065000"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Procedura: utilizzare caratteri di escape speciali in MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alcuni caratteri hanno un significato particolare nei file di progetto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Tra gli esempi di carattere sono inclusi il punto e virgola (;) e l'asterisco (*). Per un elenco completo di questi caratteri speciali, vedere [Caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Per usare questi caratteri speciali come valori letterali in un file di progetto, è necessario specificarli usando la sintassi %*xx*, dove *xx* rappresenta il valore esadecimale ASCII del carattere.  
  
## <a name="msbuild-special-characters"></a>Caratteri speciali di MSBuild  
 I caratteri speciali sono usati, ad esempio, nell'attributo `Include` degli elenchi di elementi. L'elenco di elementi seguenti, ad esempio, dichiara due elementi: `MyFile.cs` e `MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Per dichiarare un elemento che contiene un punto e virgola nel nome, è necessario usare la sintassi %*xx* per usare il carattere di escape per il punto e virgola e impedire a [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] di dichiarare due elementi separati. L'elemento seguente, ad esempio, usa il carattere di escape per il punto e virgola e dichiara un solo elemento denominato `MyFile.cs;MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Per usare un carattere speciale di MSBuild come carattere letterale  
  
- Usare la notazione %*xx* al posto del carattere speciale, dove *xx* rappresenta il valore esadecimale del carattere ASCII. Ad esempio, per usare un asterisco (*) come carattere letterale, usare il valore `%2A`.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Elementi](../msbuild/msbuild-items.md) [MSBuild](msbuild.md)
