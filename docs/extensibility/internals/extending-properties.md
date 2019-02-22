---
title: Estensione delle proprietà | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84fef8d0f63f76c7810c94ade2e1eb58e55b94cd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602975"
---
# <a name="extend-properties"></a>Estendere le proprietà
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **delle proprietà** finestra è un visualizzatore proprietà universale per i componenti COM e COM+ e supporta tutte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prodotti. Il **delle proprietà** finestra funziona con `ITypeInfo` digitare le informazioni e i metadati di COM+ per elencare le proprietà in fase di progettazione per l'oggetto attualmente selezionato in un'altra finestra nell'ambiente di sviluppo integrato (IDE).

 Il **proprietà** finestra, che può essere aperto premendo **F4** sulla tastiera, o si seleziona **finestra proprietà** nel **visualizzazione** dal menu Consente di visualizzare e modificare proprietà indipendenti dalla configurazione, in fase di progettazione e gli eventi degli oggetti selezionati. Proprietà dipendenti dalla configurazione, associate a soluzioni e progetti, vengono visualizzate nella [pagine delle proprietà](../../extensibility/internals/property-pages.md). Per altre informazioni, [gestire le opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).

 ![Panoramica della finestra proprietà](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") finestra proprietà

 In questa sezione vengono fornite informazioni dettagliate correlate a singole aree del **proprietà** finestra e le interfacce da implementare e chiamare per popolare la finestra.

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica della finestra proprietà](../../extensibility/internals/properties-window-overview.md)

 Viene illustrato lo scopo del **proprietà** finestra rispetto alla finestra degli strumenti e la finestra del documento.

- [Criteri dei modelli e la finestra proprietà](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Illustra come un progetto è contenuto in un progetto di modello dell'organizzazione e come tale progetto di modello aziendale può applicare i criteri.

- [Interfacce e i campi di proprietà finestra](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Illustra la base per la selezione che determina quali informazioni vengono visualizzate nel **proprietà** finestra.

- [Elenco di oggetti finestra proprietà](../../extensibility/internals/properties-window-object-list.md)

 Viene descritto lo scopo del **proprietà** elenco di oggetti finestra, che descrivono come, quando un oggetto diverso da questo elenco viene attivata una chiamata, l'ambiente è stato informato che sia stato selezionato un nuovo oggetto.

- [Pulsanti della finestra proprietà](../../extensibility/internals/properties-window-buttons.md)

 Viene illustrato lo scopo dei pulsanti quattro predefiniti visualizzati nei **proprietà** degli strumenti della finestra.

- [Griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md)

 Viene spiegato in cui vengono trovati i nomi di proprietà e campi di valori di proprietà nella griglia.

## <a name="related-sections"></a>Sezioni correlate
- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Vengono illustrati i progetti come i blocchi predefiniti del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Compilare](../../ide/compiling-and-building-in-visual-studio.md)

 Descrive come è possibile usare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] piattaforma per il test e debug delle applicazioni durante la compilazione.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Viene descritto il `IDispatch` interfaccia, prima di tutto è stato progettato per supportare l'automazione, che fornisce un meccanismo di associazione tardiva per accedere e recuperare informazioni sui metodi e proprietà di un oggetto.

- [Gestire le impostazioni dell'applicazione (.NET)](../../ide/managing-application-settings-dotnet.md)

 Viene fornita una panoramica delle impostazioni dell'applicazione che consentono di configurare l'applicazione in modo che i valori delle proprietà sono archiviati in un file di configurazione esterno anziché il codice dell'applicazione compilata.

- [Soluzioni e progetti](../../ide/solutions-and-projects-in-visual-studio.md)

 Viene spiegato come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce in modo efficiente gli elementi, ad esempio i riferimenti, le connessioni dati, cartelle e file necessari per l'attività di sviluppo tramite soluzioni e progetti.

- [Estendere altre parti di Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Spiega come usare i servizi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].