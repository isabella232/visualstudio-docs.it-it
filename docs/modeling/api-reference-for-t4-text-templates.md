---
title: Riferimento API per modelli di testo T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8af5f4496356b3fa349b514a4158149d6a96d684
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858986"
---
# <a name="api-reference-for-t4-text-templates"></a>Riferimento API per modelli di testo T4

L'API di creazione di modelli di testo consente di richiamare e personalizzare la trasformazione dei [modelli di testo](../modeling/code-generation-and-t4-text-templates.md).

## <a name="namespaces"></a>Spazi dei nomi

|Spazio dei nomi|Scopo|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.TextTemplating>|Contiene classi per la funzionalità di trasformazione del modello testo. Il motore di trasformazione del modello testo è integrato in Visual Studio e trasforma i file di modello di testo in file di output di testo generato.|
|<xref:Microsoft.VisualStudio.TextTemplating.Modeling>|Fornisce testo trasformazione funzionalità correlate a modelli UML e linguaggi specifici di dominio, ad esempio l'accesso a ModelBus di Visual Studio.|
|<xref:Microsoft.VisualStudio.TextTemplating.VSHost>|Fornisce l'accesso al servizio di creazione di modelli di testo in Visual Studio.|