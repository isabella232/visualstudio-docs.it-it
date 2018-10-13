---
title: Comando DslTextTransform | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1dbbf44a4adfe20f1940da32540eaad81c97251b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269373"
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform.cmd è uno script che chiama TextTransform.exe e lo esegue con opzioni comuni. È possibile usare DslTextTransformation.cmd per una compilazione notturna di automatizzare il [!INCLUDE[dsl](../includes/dsl-md.md)] progetti. Per altre informazioni, vedere [generazione di file con l'utilità di TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd si trova nella directory seguente:  
  
 **\<Percorso di installazione di Visual Studio SDK > \visualstudiointegration\tools\bin.**  
  
 È possibile specificare gli argomenti seguenti come input per DslTextTransform.cmd:  
  
-   La directory di output del progetto di modello di dominio.  
  
-   La directory di output del progetto di definizione della finestra di progettazione.  
  
-   Il percorso del file di modello di testo.  
  
 DslTextTransform.cmd elabora il file di modello di testo specificato usando i processori di direttive predefinito e gli assembly. Se si creano i processori di direttiva personalizzati, è possibile creare il proprio file batch che chiama TextTransform.exe. In questo file batch, è possibile specificare gli assembly e i processori di direttiva personalizzati associati.



