---
title: Le interfacce legacy nell'Editor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 867bef2ddf1463005e1d6b0d9ca6c508ede97014
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079507"
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfacce legacy nell'editor
Editor di Visual Studio è possibile accedere da interfacce legacy. Visual Studio SDK include schede noti come *shim*, che abilitano tali interfacce interagire con il nuovo editor. Tuttavia, è consigliabile aggiornare il codice legacy per utilizzare il nuovo editor delle API. Il codice offrirà prestazioni migliori ed è possibile usare le nuove tecnologie quali Windows Presentation Foundation (WPF) e Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Adatta il codice legacy per l'editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Viene illustrato come adattare il codice per il nuovo editor.|  
|[Comportamento nuovo o modificato con schede editor](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Viene illustrato come il comportamento delle schede dell'editor è diverso da quello delle precedenti versioni dell'editor.|  
|[All'interno dell'editor di base](../extensibility/inside-the-core-editor.md)|Descrive i diversi componenti di versioni precedenti dell'editor.|  
|[Creare un'istanza di editor principale con l'API legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Viene illustrato come usare l'API legacy per creare un'istanza di editor principale.|  
|[Factory dell'editor](../extensibility/editor-factories.md)|Viene illustrato come usare factory dell'editor con l'API legacy.|  
|[Procedura: registrare i tipi di file dell'editor](../extensibility/how-to-register-editor-file-types.md)|Spiega come collegare un'estensione di file in un editor.|  
|[Procedura dettagliata: Creazione di un core editor e registrare un tipo di file editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Viene illustrato come creare un core editor e un collegamento un'estensione di file.|  
|[Procedura: fornire il contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md)|Viene illustrato come fornire il contesto per l'editor.|  
|[Servizi di linguaggio e l'editor principale di](../extensibility/language-services-and-the-core-editor.md)|Illustra le interazioni tra un servizio di linguaggio e un editor.|  
|[Accedere al buffer di testo usando l'API legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Viene illustrato come accedere ai buffer di testo usando l'API legacy.|  
|[Visualizzazione di theText accesso usando l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Viene illustrato come accedere alla visualizzazione di testo usando l'API legacy.|  
|[Personalizzare le finestre di codice usando l'API legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Viene illustrato come personalizzare le finestre di codice usando l'API legacy.|  
|[Livelli di accesso testo usando l'API legacy](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Viene illustrato come accedere a diversi livelli di testo usando l'API legacy.|  
|[Usare marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)|Viene illustrato come aggiungere i marcatori di testo usando l'API legacy.|  
|[Personalizzare menu e controlli di editor usando l'API legacy](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Viene illustrato come personalizzare i controlli di editor usando l'API legacy.|  
|[Gestire l'annullamento e ripristino con l'API legacy](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Illustra come gestire l'annullamento e ripristino con l'API legacy.|  
|[Procedura: implementare la ricerca e sostituzione meccanismo](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Illustra come gestire Trova e Sostituisci usando l'API legacy.|  
|[Procedura: eliminare le notifiche di modifica di file](../extensibility/how-to-suppress-file-change-notifications.md)|Viene illustrato come eliminare le notifiche di modifica di file mediante l'API legacy.|  
|[Creare finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Viene illustrato come creare finestre di progettazione ed editor personalizzati.|  
|[Sviluppare un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)|Vengono forniti i collegamenti ai documenti sulle funzionalità che forniscono funzionalità di personalizzazione per la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale di aggiungendo il supporto per un servizio di linguaggio.|  
|[Usare i tipi di carattere e colori](../extensibility/using-fonts-and-colors.md)|Illustra come usare i tipi di carattere e colori con interfacce legacy.|