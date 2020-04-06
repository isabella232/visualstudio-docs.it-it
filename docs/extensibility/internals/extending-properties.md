---
title: Estensione delle proprietà . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708424"
---
# <a name="extend-properties"></a>Estendere le proprietà
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestra **Proprietà** è un visualizzatore di proprietà universale [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per i componenti COM e COM e supporta tutti i prodotti. La **Properties** finestra Proprietà `ITypeInfo` funziona con le informazioni sul tipo e i metadati COM per elencare le proprietà della fase di progettazione per l'oggetto attualmente selezionato in qualsiasi altra finestra nell'ambiente di sviluppo integrato (IDE).

 La finestra **Proprietà,** che può essere aperta premendo **F4** sulla tastiera o scegliendo **Finestra Proprietà** dal menu **Visualizza,** viene utilizzata per visualizzare e modificare le proprietà e gli eventi in fase di progettazione indipendenti dalla configurazione degli oggetti selezionati. Le proprietà dipendenti dalla configurazione, associate a soluzioni e progetti, vengono visualizzate nelle [pagine delle proprietà.](../../extensibility/internals/property-pages.md) Per ulteriori informazioni, [vedere Gestire le opzioni di configurazione.](../../extensibility/internals/managing-configuration-options.md)

 ![Panoramica della finestra Proprietà](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow (finestra di confronto)") Finestra Proprietà

 In questa sezione vengono fornite informazioni dettagliate relative alle singole aree della finestra **Proprietà** e alle interfacce che è necessario implementare e chiamare per popolare la finestra.

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica della finestra Proprietà](../../extensibility/internals/properties-window-overview.md)

 Viene illustrato lo scopo della finestra **Proprietà** relativa alla finestra degli strumenti e alla finestra del documento.

- [Criteri modello e finestra Proprietà](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Viene illustrato come un progetto è contenuto in un progetto di modello enterprise e come tale progetto di modello enterprise può applicare i criteri.

- [Campi e interfacce della finestra Proprietà](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Viene illustrata la base per la selezione che determina quali informazioni vengono visualizzate nella finestra **Proprietà.**

- [Elenco oggetti della finestra Proprietà](../../extensibility/internals/properties-window-object-list.md)

 Descrive lo scopo dell'elenco di oggetti della finestra **Proprietà,** descrivendo come, quando un oggetto diverso da questo elenco attiva una chiamata, l'ambiente viene informato che è stato selezionato un nuovo oggetto.

- [Pulsanti della finestra Proprietà](../../extensibility/internals/properties-window-buttons.md)

 Viene illustrato lo scopo dei quattro pulsanti predefiniti visualizzati nella barra degli strumenti della finestra **Proprietà.**

- [Griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md)

 Viene illustrato dove si trovano i nomi delle proprietà e i campi dei valori delle proprietà nella griglia.

## <a name="related-sections"></a>Sezioni correlate
- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Vengono illustrati i progetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] come blocchi predefiniti dell'IDE.

- [Compilazione e creazione](../../ide/compiling-and-building-in-visual-studio.md)

 Viene descritto come utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la piattaforma per il test continuo e il debug delle applicazioni durante la compilazione.

- [Idispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Viene descritta l'interfaccia, `IDispatch` che è stata inizialmente progettata per supportare l'automazione, fornendo un meccanismo ad associazione tardiva per accedere e recuperare informazioni sui metodi e le proprietà di un oggetto.

- [Gestire le impostazioni dell'applicazione (.NET)](../../ide/managing-application-settings-dotnet.md)

 Viene fornita una panoramica delle impostazioni dell'applicazione che consentono di configurare l'applicazione in modo che i valori delle proprietà vengano archiviati in un file di configurazione esterno anziché nel codice compilato dell'applicazione.

- [Soluzioni e progetti](../../ide/solutions-and-projects-in-visual-studio.md)

 Viene illustrato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] come gestire in modo efficiente gli elementi quali riferimenti, connessioni dati, cartelle e file necessari per le attività di sviluppo tramite soluzioni e progetti.

- [Estendere altre parti di Visual StudioExtend other parts of Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Spiega come usare i servizi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
