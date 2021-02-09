---
title: Estensione delle proprietà | Microsoft Docs
description: Informazioni sulle interfacce che è necessario implementare e chiamare per estendere l'elenco di proprietà in Visual Studio Finestra Proprietà.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9a777bf11f388873978f450184f1455236e9ff9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887081"
---
# <a name="extend-properties"></a>Estendi proprietà
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestra **Proprietà** è un visualizzatore di proprietà universale per i componenti com e com+ e supporta tutti i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prodotti. La finestra **Proprietà** funziona con le `ITypeInfo` informazioni sul tipo e i metadati com+ per elencare le proprietà della fase di progettazione per l'oggetto attualmente selezionato in qualsiasi altra finestra del Integrated Development Environment (IDE).

 La finestra **Proprietà** , che può essere aperta premendo **F4** sulla tastiera oppure scegliendo **finestra Proprietà** dal menu **Visualizza** , viene utilizzata per visualizzare e modificare le proprietà e gli eventi della fase di progettazione indipendenti dalla configurazione degli oggetti selezionati. Le proprietà dipendenti dalla configurazione, associate a soluzioni e progetti, vengono visualizzate nelle [pagine delle proprietà](../../extensibility/internals/property-pages.md). Per ulteriori informazioni, [gestire le opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).

 ![Panoramica di finestra Proprietà](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Finestra Proprietà

 In questa sezione vengono fornite informazioni dettagliate relative alle singole aree della finestra **Proprietà** e alle interfacce che è necessario implementare e chiamare per popolare la finestra.

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica di Finestra Proprietà](../../extensibility/internals/properties-window-overview.md)

 Viene illustrato lo scopo della finestra **Proprietà** rispetto alla finestra degli strumenti e alla finestra del documento.

- [Criterio del modello e Finestra Proprietà](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Viene illustrato il modo in cui un progetto è contenuto in un progetto modello Enterprise e il modo in cui il progetto modello Enterprise può applicare i criteri.

- [Campi e interfacce di Finestra Proprietà](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Viene illustrata la base per la selezione che determina quali informazioni vengono visualizzate nella finestra **Proprietà** .

- [Elenco oggetti Finestra Proprietà](../../extensibility/internals/properties-window-object-list.md)

 Descrive lo scopo dell'elenco di oggetti della finestra **Proprietà** , che descrive come, quando un oggetto diverso da questo elenco attiva una chiamata, l'ambiente viene informato che è stato selezionato un nuovo oggetto.

- [Pulsanti Finestra Proprietà](../../extensibility/internals/properties-window-buttons.md)

 Viene illustrato lo scopo dei quattro pulsanti predefiniti visualizzati sulla barra degli strumenti della finestra **Proprietà** .

- [Griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md)

 Viene illustrato dove vengono trovati i campi dei nomi di proprietà e dei valori delle proprietà nella griglia.

## <a name="related-sections"></a>Sezioni correlate
- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Vengono illustrati i progetti come blocchi predefiniti dell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Compilare](../../ide/compiling-and-building-in-visual-studio.md)

 Viene descritto come utilizzare la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] piattaforma per eseguire continuamente test e debug delle applicazioni durante la compilazione.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Descrive l' `IDispatch` interfaccia, che è stata progettata per supportare l'automazione, fornendo un meccanismo ad associazione tardiva per accedere e recuperare informazioni sui metodi e sulle proprietà di un oggetto.

- [Gestire le impostazioni dell'applicazione (.NET)](../../ide/managing-application-settings-dotnet.md)

 Viene fornita una panoramica delle impostazioni dell'applicazione che consentono di configurare l'applicazione in modo che i valori delle proprietà vengano archiviati in un file di configurazione esterno anziché nel codice compilato dell'applicazione.

- [Soluzioni e progetti](../../ide/solutions-and-projects-in-visual-studio.md)

 Viene illustrato come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestire in modo efficiente gli elementi, ad esempio i riferimenti, le connessioni dati, le cartelle e i file necessari per il lavoro di sviluppo tramite soluzioni e progetti.

- [Estendi altre parti di Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Spiega come usare i servizi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
