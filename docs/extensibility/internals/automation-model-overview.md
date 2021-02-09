---
title: Panoramica del modello di automazione | Microsoft Docs
description: Informazioni sul modello di automazione di Visual Studio costituito da un set di oggetti in cui è possibile scrivere un componente aggiuntivo o un'estensione di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 26184263d5f269ebf6922c5dd85a37e93356e935
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906018"
---
# <a name="automation-model-overview"></a>Panoramica del modello di automazione
Il modello di automazione è costituito da un set di oggetti in cui è possibile scrivere un componente aggiuntivo o un'estensione di Visual Studio. Un componente aggiuntivo è un'applicazione in grado di modificare l'ambiente di Visual Studio e di automatizzare le attività comuni. Un'estensione di Visual Studio può creare componenti personalizzati di Visual Studio o aggiungere alla funzionalità dei componenti standard, ad esempio l'editor di testo.

## <a name="objects-in-the-automation-model"></a>Oggetti nel modello di automazione
 Il modello di automazione è costituito da gruppi di oggetti correlati che controllano i facet principali dell'ambiente comune. Il diagramma seguente illustra il set completo di oggetti di Visual Studio che compongono il modello di automazione.

 ![Grafico degli oggetti di automazione di Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Per altre informazioni, vedere [estendere l'ambiente di Visual Studio](/previous-versions/esk3eey8(v=vs.140)).

 L'ambiente fornisce un modello per aree funzionali diverse. È ad esempio disponibile un modello di codice per vari elementi che potrebbero essere presenti nel codice. È disponibile un modello di documento per vari elementi del documento. Un'area, l'area del progetto, è di particolare interesse per i provider VSPackage. È probabile che si desideri che i nuovi tipi di progetto contribuiscano al modello di automazione in modo analogo a [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuiscano al modello di automazione. Questo processo è descritto in fornire l' [automazione per i pacchetti VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).

 Luoghi in cui è possibile estendere il modello di automazione dell'ambiente:

- Project

- Documento

- Codice

- Compilazione

Per altre informazioni sull'automazione, vedere [automazione ed estendibilità per Visual Studio](/previous-versions/visualstudio/visual-studio-2015/extensibility/extensibility-in-visual-studio?preserve-view=true&view=vs-2015). Questo documento e i documenti a cui forniscono i collegamenti consentono di prendere decisioni in merito a come fornire l'automazione per il pacchetto VSPackage.

## <a name="see-also"></a>Vedi anche
- [Procedura: creare un componente aggiuntivo](/previous-versions/80493a3w(v=vs.140))