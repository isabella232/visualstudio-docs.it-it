---
title: Icone di Visualizzazione classi e Visualizzatore oggetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e67763234ff7b3778cccabaed45fbbc0bc04d30
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620476"
---
# <a name="class-view-and-object-browser-icons"></a>Icone di Visualizzazione classi e Visualizzatore oggetti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visualizzazione classi** e **Visualizzatore oggetti** vengono visualizzate le icone che rappresentano le entità di codice, ad esempio spazi dei nomi, classi, funzioni e variabili. Nella tabella seguente vengono illustrate e descritte le icone.

|Icona|Descrizione|Icona|Descrizione|
|----------|-----------------|----------|-----------------|
|![Simbolo dello spazio dei nomi](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Spazio dei nomi|![Simbolo di dichiarazione](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Metodo o funzione|
|![Icona classe](../ide/media/vxclass-icon.gif "vxClass_Icon")|Class|![Simbolo dell'operatore](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|??|
|![Simbolo di interfaccia Lollipop](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Interfaccia|![Simbolo proprietà](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|proprietà|
|![Simbolo di struttura](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Struttura|![Icona campo](../ide/media/vxfield-icon.gif "vxField_Icon")|Campo o variabile|
|![Simbolo Unione](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Unione|![Simbolo evento](../ide/media/vxevent-icon.gif "vxEvent_Icon")|event|
|![Simbolo di enumerazione](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enum|![Icona costante](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Costante|
|![Simbolo di definizione del tipo](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|TypeDef|![Simbolo enumera elemento](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Elemento di enumerazione|
|![Simbolo del modulo di Visual Studio](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Modulo|![Simbolo elemento mappa](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Elemento mappa|
|![Simbolo del metodo di estensione](../ide/media/extensionmethod.gif "ExtensionMethod")|Metodo di estensione|![Simbolo di dichiarazione](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Dichiarazione esterna|
|![Simbolo delegato](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|delegato|![Icona di errore per Visualizzazione classi e Visualizzatore oggetti](../ide/media/erroricon.gif "ErrorIcon")|Error|
|![Simbolo di eccezione](../ide/media/vxexception-icon.gif "vxException_Icon")|Eccezione|![Simbolo del modello](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Modello|
|![Simbolo mappa](../ide/media/vxmap-icon.gif "vxMap_Icon")|Mappa|![Simbolo punto esclamativo errore](../ide/media/vxerror-icon.gif "vxError_Icon")|Sconosciuto|
|![Simbolo di invio del tipo](../ide/media/ob-type-forward.gif "ob_type_forward")|Inoltro del tipo|||

## <a name="signal-icons"></a>icone di segnalazione
 Le icone di segnalazione seguenti si applicano a tutte le icone precedenti e ne indicano l'accessibilità.

> [!NOTE]
> Se il progetto è incluso in un database di controllo del codice sorgente potrebbero essere visualizzate altre icone di segnalazione per indicare lo stato di controllo del codice sorgente, ad esempio se il codice è stato archiviato o estratto.

|Icona|Descrizione|
|----------|-----------------|
|\<Nessuna icona di segnalazione>|Pubblico. Accessibile ovunque in questo componente e da qualsiasi componente che vi fa riferimento.|
|![Simbolo protetto da segnale](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Protetto. Accessibile dalla classe o dal tipo contenitore o da quelli da essi derivati.|
|![Simbolo privato del segnale](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Privato. Accessibile solo nella classe o nel tipo contenitore.|
|![Simbolo sealed Signal](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Contrassegnato come sealed.|
|![Simbolo&#47;interno dell'elemento Signal](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Friend/Internal. Accessibile solo dal progetto.|
|![Freccia icona segnale](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Collegamento. Un collegamento all'oggetto.|

## <a name="see-also"></a>Vedere anche
 [Visualizzazione della struttura del codice](../ide/viewing-the-structure-of-code.md)
