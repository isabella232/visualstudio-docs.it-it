---
title: Comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: db916372691ce5e336e142aeb72288193e1ed807
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947053"
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
DslTextTransform.cmd è uno script che chiama TextTransform.exe e viene eseguito con le opzioni comuni. È possibile utilizzare DslTextTransformation.cmd per una compilazione notturna di automatizzare il [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] progetti. Per ulteriori informazioni, vedere [la generazione di file con l'utilità di TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd si trova nella directory seguente:

 **\<Percorso di installazione di Visual Studio SDK > \visualstudiointegration\tools\bin.**

 È possibile specificare gli argomenti seguenti come input per DslTextTransform.cmd:

-   La directory di output del progetto di modello di dominio.

-   La directory di output del progetto di definizione della finestra di progettazione.

-   Il percorso del file di modello di testo.

 DslTextTransform.cmd elabora il file di modello di testo specificato con i processori di direttive predefinito e gli assembly. Se si creano i processori di direttiva personalizzati, è possibile creare un file batch che chiama TextTransform.exe. In questo file batch, è possibile specificare gli assembly e i processori di direttiva personalizzati associati.