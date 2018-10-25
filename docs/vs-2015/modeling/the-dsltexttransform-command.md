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
ms.openlocfilehash: 882d2c8d0dec5e4673b24436067bd6255c2052be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853155"
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform.cmd è uno script che chiama TextTransform.exe e lo esegue con opzioni comuni. È possibile usare DslTextTransformation.cmd per una compilazione notturna di automatizzare il [!INCLUDE[dsl](../includes/dsl-md.md)] progetti. Per altre informazioni, vedere [generazione di file con l'utilità di TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd si trova nella directory seguente:  
  
 **\<Percorso di installazione di Visual Studio SDK > \visualstudiointegration\tools\bin.**  
  
 È possibile specificare gli argomenti seguenti come input per DslTextTransform.cmd:  
  
- La directory di output del progetto di modello di dominio.  
  
- La directory di output del progetto di definizione della finestra di progettazione.  
  
- Il percorso del file di modello di testo.  
  
  DslTextTransform.cmd elabora il file di modello di testo specificato usando i processori di direttive predefinito e gli assembly. Se si creano i processori di direttiva personalizzati, è possibile creare il proprio file batch che chiama TextTransform.exe. In questo file batch, è possibile specificare gli assembly e i processori di direttiva personalizzati associati.



