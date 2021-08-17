---
title: Estensione delle proprietà | Microsoft Docs
description: Informazioni sulle interfacce che è necessario implementare e chiamare per estendere l'elenco di proprietà nel Visual Studio Finestra Proprietà.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3f631e09287c6d28aa61ea7832d3f4d5241548e1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063473"
---
# <a name="extend-properties"></a>Estendere le proprietà
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **finestra Proprietà** è un visualizzatore proprietà universale per i componenti COM e COM+ e supporta tutti i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prodotti. La **finestra Proprietà** funziona con informazioni sul tipo e metadati COM+ per elencare le proprietà in fase di progettazione per l'oggetto attualmente selezionato in qualsiasi altra finestra nell'ambiente di sviluppo integrato `ITypeInfo` (IDE).

 La **finestra** Proprietà, che può essere aperta premendo **F4** sulla tastiera o scegliendo Finestra Proprietà dal **menu** Visualizza, consente di visualizzare e modificare proprietà ed eventi di oggetti selezionati indipendenti dalla configurazione e in fase di progettazione.  Le proprietà dipendenti dalla configurazione, associate a soluzioni e progetti, vengono visualizzate nelle [pagine delle proprietà](../../extensibility/internals/property-pages.md). Per altre informazioni, vedere [Gestire le opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).

 ![Finestra Proprietà panoramica](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Finestra Proprietà

 In questa sezione vengono fornite informazioni dettagliate  relative alle singole aree della finestra Proprietà e alle interfacce che è necessario implementare e chiamare per popolare la finestra.

## <a name="in-this-section"></a>Contenuto della sezione
- [Finestra Proprietà panoramica](../../extensibility/internals/properties-window-overview.md)

 Illustra lo scopo della finestra **Proprietà** relativa alla finestra degli strumenti e alla finestra del documento.

- [Criteri di modello e Finestra Proprietà](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Viene illustrato come un progetto è contenuto in un progetto modello Enterprise e come tale progetto modello enterprise può applicare i criteri.

- [Finestra Proprietà e interfacce](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Illustra la base per la selezione che determina le informazioni visualizzate nella **finestra** Proprietà.

- [Finestra Proprietà di oggetti](../../extensibility/internals/properties-window-object-list.md)

 Descrive lo scopo  dell'elenco di oggetti della finestra Proprietà, che descrive come, quando un oggetto diverso da questo elenco attiva una chiamata, l'ambiente viene informato che è stato selezionato un nuovo oggetto.

- [Finestra Proprietà pulsanti](../../extensibility/internals/properties-window-buttons.md)

 Illustra lo scopo dei quattro pulsanti predefiniti visualizzati sulla barra degli strumenti **della finestra** Proprietà.

- [Griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md)

 Spiega dove si trovano i nomi delle proprietà e i campi dei valori delle proprietà nella griglia.

## <a name="related-sections"></a>Sezioni correlate
- [Project tipi](../../extensibility/internals/project-types.md)

 Vengono illustrati i progetti come blocchi predefiniti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'IDE.

- [Compilare](../../ide/compiling-and-building-in-visual-studio.md)

 Viene descritto come usare la piattaforma per il test e il debug continuo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] delle applicazioni durante la compilazione.

- [Idispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Viene descritta l'interfaccia , progettata per supportare l'automazione, fornendo un meccanismo ad associazione tardiva per accedere e recuperare informazioni sui metodi e le proprietà `IDispatch` di un oggetto.

- [Gestire le impostazioni dell'applicazione (.NET)](../../ide/managing-application-settings-dotnet.md)

 Fornisce una panoramica delle impostazioni dell'applicazione che consentono di configurare l'applicazione in modo che i valori delle proprietà siano archiviati in un file di configurazione esterno anziché nel codice compilato dell'applicazione.

- [Soluzioni e progetti](../../ide/solutions-and-projects-in-visual-studio.md)

 Spiega in che modo gestisce in modo efficiente gli elementi, ad esempio riferimenti, connessioni dati, cartelle e file, necessari per lo sviluppo tramite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] soluzioni e progetti.

- [Estendere altre parti di Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Spiega come usare i servizi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
