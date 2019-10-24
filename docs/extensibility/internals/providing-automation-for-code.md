---
title: Fornire l'automazione per il codice | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 874446aa6bf2e40a120aac49e7d91fd3d861d1d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724971"
---
# <a name="providing-automation-for-code"></a>Automazione per il codice
La creazione di un modello di automazione per il codice non è obbligatoria. L'SDK dell'ambiente non fornisce un esempio per questa operazione. Per informazioni dettagliate sui modelli di codice, vedere l'oggetto <xref:EnvDTE.CodeModel>.

 Per implementare un modello di codice, è necessario implementare le interfacce determinate dalla struttura dei dati interna. Gli oggetti devono essere derivati dalla classe `IDispatch`.

 Gli oggetti estesi, <xref:EnvDTE.CodeModel> e <xref:EnvDTE.FileCodeModel>, sono disponibili dall'oggetto <xref:EnvDTE.Project> e hanno un aspetto simile al seguente:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 È possibile scegliere di implementare solo la `CodeModel` o l'interfaccia `FileCodeModel` nell'oggetto restituito dagli oggetti `Project` e <xref:EnvDTE.ProjectItem>. Fornire tutte le funzionalità di questa interfaccia appropriate per il sistema del progetto.

 Se si desidera aggiungere funzionalità, ad esempio metodi o proprietà, che non sono disponibili dalle interfacce standard `CodeModel` e `FileCodeModel`, creare un'interfaccia personalizzata che erediti dallo standard. Assicurarsi di documentarlo con il sistema di progetto in modo che gli utenti finali conoscano la ricerca. Viene restituita l'interfaccia standard, ma l'utente può chiamare il metodo `QueryInterface` o eseguire il cast all'interfaccia se è noto.

## <a name="see-also"></a>Vedere anche
- [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)