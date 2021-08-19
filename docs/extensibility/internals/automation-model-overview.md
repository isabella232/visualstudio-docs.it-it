---
title: Panoramica del modello di automazione | Microsoft Docs
description: Informazioni sul modello Visual Studio di automazione che è costituito da un set di oggetti in cui è possibile scrivere Visual Studio componente aggiuntivo o estensione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ed2f1491b9e692662de282e6f78f9f44c59aa5d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159347"
---
# <a name="automation-model-overview"></a>Panoramica del modello di automazione
Il modello di automazione è costituito da un set di oggetti in cui è possibile scrivere Visual Studio componente aggiuntivo o estensione. Un componente aggiuntivo è un'applicazione in grado di modificare l'ambiente Visual Studio e automatizzare le attività comuni. Un Visual Studio estensione può creare componenti Visual Studio personalizzati o aggiungere alla funzionalità dei componenti standard, ad esempio l'editor di testo.

## <a name="objects-in-the-automation-model"></a>Oggetti nel modello di automazione
 Il modello di automazione è costituito da gruppi correlati di oggetti che controllano i facet principali dell'ambiente comune. Il diagramma seguente illustra l'ampio set di oggetti Visual Studio che costituiscono il modello di automazione.

 ![Visual Studio di oggetti di automazione](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Per altre informazioni, vedere [Estendere l'ambiente Visual Studio .](/previous-versions/esk3eey8(v=vs.140))

 L'ambiente fornisce un modello per diverse aree funzionali. Ad esempio, è disponibile un modello di codice per vari elementi che è possibile trovare nel codice. È disponibile un modello di documento per vari elementi del documento. Un'area, l'area del progetto, è di particolare interesse per i provider VSPackage. È probabile che si desideri che i nuovi tipi di progetto contribuiscano al modello di automazione in modo molto uguale a quello del modello di automazione e [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuiscano al modello di automazione. Questo processo è descritto in Fornire [l'automazione per i pacchetti VSPackage.](../../extensibility/internals/providing-automation-for-vspackages.md)

 Posizioni in cui è possibile prendere in considerazione l'estensione del modello di automazione dell'ambiente:

- Project

- Documento

- Codice

- Compilazione

Per altre informazioni sull'automazione, vedere [Automazione ed estendibilità per Visual Studio](/previous-versions/visualstudio/visual-studio-2015/extensibility/extensibility-in-visual-studio?preserve-view=true&view=vs-2015). Questo documento e i documenti a cui fornisce collegamenti consentono di prendere decisioni relative a come è consigliabile fornire l'automazione per il pacchetto VSPackage.

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un componente aggiuntivo](/previous-versions/80493a3w(v=vs.140))