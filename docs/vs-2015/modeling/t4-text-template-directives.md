---
title: T4 Direttive di modello di testo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 83
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e079b21c3a85f883351808b8defda6d0d68619f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527996"
---
# <a name="t4-text-template-directives"></a>Direttive di modello di testo T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [direttive di modello di testo T4](https://docs.microsoft.com/visualstudio/modeling/t4-text-template-directives).  
  
Le direttive forniscono istruzioni al motore di trasformazione del modello di testo.  
  
 La sintassi per le direttive è la seguente:  
  
```  
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>  
```  
  
 Tutti i valori di attributo devono essere racchiusi tra virgolette doppie. Se il valore stesso contiene virgolette, è necessario applicare loro il carattere di escape \.  
  
 Le direttive sono in genere i primi elementi di un file modello o di un file incluso. Tali elementi non devono essere inseriti in un blocco di codice `<#...#>`, né dopo un blocco della funzionalità di classe `<#+...#>`.  
  
 [Direttiva template T4](../modeling/t4-template-directive.md)  
 ```  
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 [Direttiva parameter T4](../modeling/t4-parameter-directive.md)  
 ```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 [Direttiva output T4](../modeling/t4-output-directive.md)  
 ```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 [Direttiva assembly T4](../modeling/t4-assembly-directive.md)  
 ```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 [Direttiva import T4](../modeling/t4-import-directive.md)  
 ```  
<#@ import namespace="namespace" #>  
```  
  
 [Direttiva include T4](../modeling/t4-include-directive.md)  
 ```  
<#@ include file="filePath" #>  
```  
  
 [Direttiva T4 CleanUpBehavior](../modeling/t4-cleanupbehavior-directive.md)  
 ```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 È inoltre possibile creare direttive personalizzate. Per altre informazioni, vedere [creazione di processori direttiva di modelli di Custom T4 testo](../modeling/creating-custom-t4-text-template-directive-processors.md). Se si utilizza l'SDK di visualizzazione e modellazione per creare un linguaggio DSL, verrà generato un processore di direttiva come parte di tale linguaggio DSL.



