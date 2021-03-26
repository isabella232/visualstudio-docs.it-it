---
title: Supporto di più visualizzazioni documento | Microsoft Docs
description: Informazioni su come fornire più di una visualizzazione di un documento usando dati di documenti e oggetti visualizzazione documento distinti per l'editor personalizzato in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e54ee028c6a7db2d5d2ea1ab609be6c2887c9829
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056207"
---
# <a name="supporting-multiple-document-views"></a>Supporto di più visualizzazioni documento
È possibile fornire più di una visualizzazione di un documento creando oggetti dati del documento e oggetti visualizzazione documento distinti per l'editor. Alcuni casi in cui è utile una visualizzazione del documento aggiuntiva sono:

- Supporto per la nuova finestra: si desidera che l'editor fornisca due o più visualizzazioni dello stesso tipo, in modo che un utente che dispone già di una finestra aperta nell'Editor possa aprire una nuova finestra selezionando il comando **nuova finestra** dal menu **finestra** .

- Supporto per il form e la visualizzazione del codice: si desidera che l'editor fornisca visualizzazioni di tipi diversi. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], ad esempio, fornisce una visualizzazione form e una visualizzazione codice.

  Per ulteriori informazioni, vedere la procedura CreateEditorInstance nel file EditorFactory. cs nel progetto di editor personalizzato creato dal modello di pacchetto di Visual Studio. Per ulteriori informazioni su questo progetto, vedere [procedura dettagliata: creazione di un editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Sincronizzazione di viste
 Quando si implementano più visualizzazioni, l'oggetto dati del documento è responsabile di mantenere tutte le visualizzazioni sincronizzate con i dati. È possibile utilizzare le interfacce di gestione degli eventi su <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> per sincronizzare più visualizzazioni con i dati.

 Se non si utilizza l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto per sincronizzare più visualizzazioni, è necessario implementare il proprio sistema di eventi per gestire le modifiche apportate all'oggetto dati del documento. È possibile utilizzare livelli di granularità diversi per rendere aggiornate più visualizzazioni. Con un'impostazione della granularità massima, quando si digita una visualizzazione, le altre visualizzazioni vengono aggiornate immediatamente. Con la granularità minima, altre viste non vengono aggiornate finché non vengono attivate.

## <a name="determining-whether-document-data-is-already-open"></a>Determinare se i dati del documento sono già aperti
 La tabella documenti in esecuzione (RDT) nel Integrated Development Environment (IDE) consente di rilevare se i dati per un documento sono già aperti, come illustrato nella figura seguente.

 ![Immagine di DocDataView](../extensibility/media/docdataview.gif "Docdataview") Visualizzazioni multiple

 Per impostazione predefinita, ogni visualizzazione (oggetto visualizzazione documento) è contenuta nella relativa cornice di finestra ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> ). Come già indicato, tuttavia, i dati del documento possono essere visualizzati in più visualizzazioni. Per abilitare questa operazione, Visual Studio controlla il RDT per determinare se il documento in questione è già aperto in un editor. Quando l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> per creare l'editor, un valore non null restituito nel `punkDocDataExisting` parametro indica che il documento è già aperto in un altro editor. Per ulteriori informazioni sul funzionamento delle funzioni RDT, vedere [esecuzione di una tabella documenti](../extensibility/internals/running-document-table.md).

 Nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementazione di esaminare l'oggetto dati del documento restituito in `punkDocDataExisting` per determinare se i dati del documento sono appropriati per l'editor. Ad esempio, solo i dati HTML devono essere visualizzati da un editor HTML. Se è appropriato, la factory dell'editor deve fornire una seconda visualizzazione per i dati. Se il `punkDocDataExisting` parametro non è `NULL` , è possibile che l'oggetto dati del documento sia aperto in un altro editor o, più probabilmente, che i dati del documento siano già aperti in una visualizzazione diversa con lo stesso editor. Se i dati del documento sono aperti in un editor diverso che non è supportato dalla factory dell'editor, Visual Studio non è in grado di aprire la factory dell'editor. Per altre informazioni, vedere [procedura: aggiungere visualizzazioni ai dati del documento](../extensibility/how-to-attach-views-to-document-data.md).
