---
title: Le interfacce legacy nell'Editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8483068ae03c9a57fc67b528393e5d6830c3ec33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180284"
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfacce legacy nell'editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor di Visual Studio è possibile accedere da interfacce legacy. Visual Studio SDK include schede noti come *shim*, che abilitano tali interfacce interagire con il nuovo editor. Tuttavia, è consigliabile aggiornare il codice legacy per utilizzare il nuovo editor delle API. Il codice offrirà prestazioni migliori ed è possibile usare le nuove tecnologie quali Windows Presentation Foundation (WPF) e Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Adattamento del codice legacy all'editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Viene illustrato come adattare il codice per il nuovo editor.|  
|[Comportamento nuovo o modificato con gli adattatori di editor](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Viene illustrato come il comportamento delle schede dell'editor è diverso da quello delle precedenti versioni dell'editor.|  
|[Componenti e funzionalità dell'editor principale](../extensibility/inside-the-core-editor.md)|Descrive i diversi componenti di versioni precedenti dell'editor.|  
|[Creazione di un'istanza dell'editor principale tramite l'API legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Viene illustrato come usare l'API legacy per creare un'istanza di editor principale.|  
|[Factory editor](../extensibility/editor-factories.md)|Viene illustrato come usare factory dell'editor con l'API legacy.|  
|[Procedura: registrare i tipi di file dell'editor](../extensibility/how-to-register-editor-file-types.md)|Spiega come collegare un'estensione di file in un editor.|  
|[Procedura dettagliata: creazione di un editor principale e registrazione di un tipo di file dell'editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Viene illustrato come creare un core editor e un collegamento un'estensione di file.|  
|[Procedura: fornire il contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md)|Viene illustrato come fornire il contesto per l'editor.|  
|[Servizi di linguaggio ed editor principale](../extensibility/language-services-and-the-core-editor.md)|Illustra le interazioni tra un servizio di linguaggio e un editor.|  
|[Accesso al buffer di testo tramite l'API legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Viene illustrato come accedere ai buffer di testo usando l'API legacy.|  
|[Accesso alla visualizzazione testo tramite l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Viene illustrato come accedere alla visualizzazione di testo usando l'API legacy.|  
|[Personalizzazione delle finestre di codice tramite l'API legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Viene illustrato come personalizzare le finestre di codice usando l'API legacy.|  
|[Accesso ai livelli di testo tramite l'API legacy](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Viene illustrato come accedere a diversi livelli di testo usando l'API legacy.|  
|[Uso di marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)|Viene illustrato come aggiungere i marcatori di testo usando l'API legacy.|  
|[Personalizzazione dei controlli e dei menu dell'editor tramite l'API legacy](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Viene illustrato come personalizzare i controlli di editor usando l'API legacy.|  
|[Gestione delle fase di rollback e di rollforward tramite l'API legacy](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Illustra come gestire l'annullamento e ripristino con l'API legacy.|  
|[Procedura: implementare il meccanismo di ricerca e sostituzione](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Illustra come gestire Trova e Sostituisci usando l'API legacy.|  
|[Procedura: eliminare le notifiche di modifica file](../extensibility/how-to-suppress-file-change-notifications.md)|Viene illustrato come eliminare le notifiche di modifica di file mediante l'API legacy.|  
|[Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Viene illustrato come creare finestre di progettazione ed editor personalizzati.|  
|[Sviluppo di un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)|Vengono forniti i collegamenti ai documenti sulle funzionalità che forniscono funzionalità di personalizzazione per la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale di aggiungendo il supporto per un servizio di linguaggio.|  
|[Uso di tipi di carattere e colori](../extensibility/using-fonts-and-colors.md)|Illustra come usare i tipi di carattere e colori con interfacce legacy.|
