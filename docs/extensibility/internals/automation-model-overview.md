---
title: Cenni preliminari sul modello di automazione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710014"
---
# <a name="automation-model-overview"></a>Panoramica del modello di automazione
Il modello di automazione è costituito da un set di oggetti su cui è possibile scrivere un componente aggiuntivo o un'estensione di Visual Studio.The automation model consists of a set of objects against which you can write a Visual Studio add-in or extension. Un componente aggiuntivo è un'applicazione che può modificare l'ambiente di Visual Studio e automatizzare le attività comuni. Un'estensione di Visual Studio può creare componenti personalizzati di Visual Studio o aggiungere alla funzionalità dei componenti standard, ad esempio l'editor di testo.

## <a name="objects-in-the-automation-model"></a>Oggetti nel modello di automazioneObjects in the automation model
 Il modello di automazione è costituito da gruppi correlati di oggetti che controllano i principali aspetti dell'ambiente comune. Nel diagramma seguente viene illustrato il set completo di oggetti di Visual Studio che compongono il modello di automazione.

 ![Grafico degli oggetti di automazione di Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Per ulteriori informazioni, vedere [Estendere l'ambiente di Visual Studio.](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)

 L'ambiente fornisce un modello per diverse aree funzionali. Ad esempio, è disponibile un modello di codice per vari elementi che è possibile trovare nel codice. Esiste un modello di documento per vari elementi del documento. Un'area, l'area del progetto, è di particolare interesse per i provider VSPackage. È probabile che si desideri che i nuovi tipi di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuiscano al modello di automazione in modo molto simile a quello e al modello di automazione. Tale processo è descritto in [fornire l'automazione per VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).

 Posizioni in cui è possibile considerare l'estensione del modello di automazione dell'ambiente:

- Project

- Document

- Codice

- Compilazione

Per ulteriori informazioni sull'automazione, vedere [automazione ed estensibilità per Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Questo documento e i documenti a cui fornisce collegamenti, consentono di prendere decisioni su come è necessario fornire l'automazione per il pacchetto VSPackage.This document and the documents it provides links to, help you make decisions regarding how you should provide automation for your VSPackage.

## <a name="see-also"></a>Vedere anche
- [Procedura: creare un componente aggiuntivoHow to: Create an add-in](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
