---
title: Comando DslTextTransform | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: "30"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 4b8c7040cabf05b30920654996891bc8d19f42db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
DslTextTransform.cmd è uno script che chiama TextTransform.exe e viene eseguito con le opzioni comuni. È possibile utilizzare DslTextTransformation.cmd per una compilazione notturna di automatizzare il [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] progetti. Per ulteriori informazioni, vedere [la generazione di file con l'utilità di TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd si trova nella directory seguente:  
  
 **\<Il percorso di installazione di Visual Studio SDK > \visualstudiointegration\tools\bin.**  
  
 È possibile specificare gli argomenti seguenti come input per DslTextTransform.cmd:  
  
-   La directory di output del progetto di modello di dominio.  
  
-   La directory di output del progetto di definizione della finestra di progettazione.  
  
-   Il percorso del file di modello di testo.  
  
 DslTextTransform.cmd elabora il file di modello di testo specificato con i processori di direttive predefinito e gli assembly. Se si creano i processori di direttiva personalizzati, è possibile creare un file batch che chiama TextTransform.exe. In questo file batch, è possibile specificare gli assembly e i processori di direttiva personalizzati associati.