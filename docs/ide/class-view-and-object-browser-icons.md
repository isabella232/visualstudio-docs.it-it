---
title: Icone di Visualizzazione classi e Visualizzatore oggetti
description: Informazioni sulle Visualizzazione classi e sul Visualizzatore oggetti che rappresentano entità di codice, ad esempio spazi dei nomi, classi, funzioni e variabili.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2eb3189afe60dbd2f797846afcd404fe487d6fb9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124243"
---
# <a name="class-view-and-object-browser-icons"></a>Icone di Visualizzazione classi e Visualizzatore oggetti

In **Visualizzazione classi** e **Visualizzatore oggetti** vengono visualizzate le icone che rappresentano le entità di codice, ad esempio spazi dei nomi, classi, funzioni e variabili. Nella tabella seguente vengono illustrate e descritte le icone.

|Icona|Descrizione|Icona|Descrizione|
|----------|-----------------|----------|-----------------|
|![Simbolo dello spazio dei nomi](../ide/media/vxnamespace_icon.gif)|Spazio dei nomi|![Simbolo Dichiarazione](../ide/media/vxmethod_icon.gif)|Metodo o funzione|
|![Icona Classe](../ide/media/vxclass_icon.gif)|Classe|![Simbolo operatore](../ide/media/vxoperator_icon.gif)|Operatore|
|![Simbolo interfaccia cerchio-linea](../ide/media/vxinterface_icon.gif)|Interfaccia|![Simbolo della proprietà](../ide/media/vxproperty_icon.gif)|Proprietà|
|![Simbolo struttura](../ide/media/vxstruct_icon.gif)|Struttura|![Icona Campo](../ide/media/vxfield_icon.gif)|Campo o variabile|
|![Simbolo unione](../ide/media/vxunion_icon.gif)|Union|![Simbolo Evento](../ide/media/vxevent_icon.gif)|Event|
|![Simbolo di enumerazione](../ide/media/vxenum_icon.gif)|Enumerazione|![Icona Costante](../ide/media/vxconstant_icon.gif)|Costante|
|![Simbolo definizione dei tipi](../ide/media/vxtypedef_icon.gif)|TypeDef|![Simbolo di enumerazione elementi](../ide/media/vxenumitem_icon.gif)|Elemento di enumerazione|
|![Simbolo dei moduli di Visual Studio](../ide/media/vxmodule_icon.gif)|Modulo|![Simbolo elemento mappa](../ide/media/vxmapitem_icon.gif)|Elemento mappa|
|![Simbolo del metodo di estensione](../ide/media/extensionmethod.gif)|Metodo di estensione|![Simbolo Dichiarazione](../ide/media/vxmethod_icon.gif)|Dichiarazione esterna|
|![Simbolo delegato](../ide/media/vxdelegate_icon.gif)|Delegato|![Icona di errore per Visualizzazione classi e Visualizzatore oggetti](../ide/media/erroricon.gif)|Errore|
|![Simbolo Eccezione](../ide/media/vxexception_icon.gif)|Eccezione|![Simbolo modello](../ide/media/vxtemplate_icon.gif)|Modello|
|![Simbolo Mappa](../ide/media/vxmap_icon.gif)|Mappa|![Simbolo di errore con punto esclamativo](../ide/media/vxerror_icon.gif)|Sconosciuto|
|![Simbolo Inoltro dei tipi](../ide/media/ob_type_forward.gif)|Inoltro del tipo|||

> [!TIP]
> Per visualizzare al meglio le icone in questa pagina, assicurarsi che il tema Microsoft Docs sia impostato su **Chiaro.** È possibile attivare o disattivare questo tema colori dal controllo che si trova nella parte inferiore sinistra della pagina, come illustrato nello screenshot seguente:
>
> ![Tema docs](../ide/media/toggle-docs-color-theme.png "Attivare o disattivare il tema colori Microsoft Docs pagine")

## <a name="signal-icons"></a>Icone di segnalazione

Le icone di segnalazione seguenti si applicano a tutte le icone precedenti e ne indicano l'accessibilità.

|Icona|Descrizione|
|----------|-----------------|
|\<No Signal Icon>|Pubblica. Accessibile ovunque in questo componente e da qualsiasi componente che vi fa riferimento.|
|![Simbolo segnale protetto](../ide/media/vxsignal_icon_key.gif)|Protetto. Accessibile dalla classe o dal tipo contenitore o da quelli da essi derivati.|
|![Simbolo segnale privato](../ide/media/vxsignal_icon_lock.gif)|Privata. Accessibile solo nella classe o nel tipo contenitore.|
|![Simbolo segnale sigillato](../ide/media/vxsignal_icon_envelope.gif)|Contrassegnato come sealed.|
|![Simbolo segnale Friend&#47;Internal](../ide/media/vxsignal_icon_diamond.gif)|Friend/Internal. Accessibile solo dal progetto.|
|![Freccia icona di segnalazione](../ide/media/vxsignal_icon_arrow.gif)|Collegamento. Un collegamento all'oggetto.|

> [!NOTE]
> Se il progetto è incluso in un database di controllo del codice sorgente potrebbero essere visualizzate altre icone di segnalazione per indicare lo stato di controllo del codice sorgente, ad esempio se il codice è stato archiviato o estratto.

> [!TIP]
> Per visualizzare altre immagini e icone dell'applicazione visualizzate in Visual Studio, scaricare la raccolta Visual Studio [**immagini.**](https://www.microsoft.com/download/details.aspx?id=35825)

## <a name="see-also"></a>Vedi anche

- [Visualizzazione della struttura del codice](../ide/viewing-the-structure-of-code.md)
