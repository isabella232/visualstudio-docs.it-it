---
title: 'Procedura: Usare caratteri di escape per caratteri speciali in MSBuild | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: "12"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 1713416665dcdb4970b6a74eb4f1e66164078cdd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Procedura: utilizzare caratteri di escape speciali in MSBuild
Alcuni caratteri hanno un significato particolare nei file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Tra gli esempi di carattere sono inclusi il punto e virgola (;) e l'asterisco (*). Per un elenco completo di questi caratteri speciali, vedere [Caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Per usare questi caratteri speciali come valori letterali in un file di progetto, è necessario specificarli usando la sintassi %*xx*, dove *xx* rappresenta il valore esadecimale ASCII del carattere.  
  
## <a name="msbuild-special-characters"></a>Caratteri speciali di MSBuild  
 I caratteri speciali sono usati, ad esempio, nell'attributo `Include` degli elenchi di elementi. L'elenco di elementi seguenti, ad esempio, dichiara due elementi: `MyFile.cs` e `MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Per dichiarare un elemento che contiene un punto e virgola nel nome, è necessario usare la sintassi %*xx* per usare il carattere di escape per il punto e virgola e impedire a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di dichiarare due elementi separati. L'elemento seguente, ad esempio, usa il carattere di escape per il punto e virgola e dichiara un solo elemento denominato `MyFile.cs;MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Per usare un carattere speciale di MSBuild come carattere letterale  
  
-   Usare la notazione %*xx* al posto del carattere speciale, dove *xx* rappresenta il valore esadecimale del carattere ASCII. Ad esempio, per usare un asterisco (*) come carattere letterale, usare il valore `%2A`.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Elementi](../msbuild/msbuild-items.md) [MSBuild](../msbuild/msbuild.md)