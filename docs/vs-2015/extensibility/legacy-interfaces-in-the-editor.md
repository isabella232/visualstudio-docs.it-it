---
title: Interfacce legacy nell'editor | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180284"
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfacce legacy nell'editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile accedere all'editor di Visual Studio dalle interfacce legacy. Visual Studio SDK include adattatori noti come *shim*, che consentono a queste interfacce di interagire con il nuovo editor. Tuttavia, è consigliabile aggiornare il codice legacy per usare la nuova API dell'editor. Il codice produrrà prestazioni migliori ed è possibile utilizzare nuove tecnologie come il Windows Presentation Foundation (WPF) e il Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Adattamento del codice legacy all'editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Viene illustrato come adattare il codice al nuovo editor.|  
|[Comportamento nuovo o modificato con gli adattatori di editor](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Spiega in che modo il comportamento degli adattatori dell'editor è diverso da quello delle versioni precedenti dell'editor.|  
|[Analisi dell'editor principale](../extensibility/inside-the-core-editor.md)|Vengono descritti i diversi componenti delle versioni precedenti dell'editor.|  
|[Creazione di un'istanza dell'editor principale tramite l'API legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Viene illustrato come usare l'API legacy per creare un'istanza dell'editor principale.|  
|[Factory editor](../extensibility/editor-factories.md)|Viene illustrato come usare le factory dell'editor con l'API legacy.|  
|[Procedura: Registrare i tipi di file dell'editor](../extensibility/how-to-register-editor-file-types.md)|Viene illustrato come collegare un'estensione del nome di file all'editor.|  
|[Procedura dettagliata: Creazione di un editor principale e registrazione di un tipo di file dell'editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Viene illustrato come creare un editor principale e collegarvi un'estensione di file.|  
|[Procedura: Fornire il contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md)|Viene illustrato come fornire il contesto per l'editor.|  
|[Servizi di linguaggio ed editor principale](../extensibility/language-services-and-the-core-editor.md)|Illustra le interazioni tra un servizio di linguaggio e un editor.|  
|[Accesso al buffer di testo tramite l'API legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Viene illustrato come accedere al buffer di testo tramite l'API legacy.|  
|[Accesso alla visualizzazione testo tramite l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Viene illustrato come accedere alla visualizzazione di testo tramite l'API legacy.|  
|[Personalizzazione delle finestre di codice tramite l'API legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Viene illustrato come personalizzare le finestre del codice usando l'API legacy.|  
|[Accesso ai livelli di testo tramite l'API legacy](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Viene illustrato come accedere a diversi livelli di testo tramite l'API legacy.|  
|[Uso di marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)|Viene illustrato come aggiungere marcatori di testo tramite l'API legacy.|  
|[Personalizzazione dei controlli e dei menu dell'editor tramite l'API legacy](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Viene illustrato come personalizzare i controlli dell'editor tramite l'API legacy.|  
|[Gestione delle fasi di rollback e di rollforward tramite l'API legacy](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Viene illustrato come gestire le operazioni di annullamento e ripristino usando l'API legacy.|  
|[Procedura: Implementare il meccanismo di ricerca e sostituzione](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Viene illustrato come gestire la ricerca e la sostituzione tramite l'API legacy.|  
|[Procedura: Eliminare le notifiche di modifica file](../extensibility/how-to-suppress-file-change-notifications.md)|Viene illustrato come disattivare le notifiche di modifica dei file tramite l'API legacy.|  
|[Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Viene illustrato come creare editor e finestre di progettazione personalizzati.|  
|[Sviluppo di un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)|Vengono forniti collegamenti ai documenti sulle funzionalità che forniscono funzionalità di personalizzazione all' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale mediante l'aggiunta del supporto per un servizio di linguaggio.|  
|[Uso di tipi di carattere e colori](../extensibility/using-fonts-and-colors.md)|Viene illustrato come usare i tipi di carattere e i colori con le interfacce legacy.|
