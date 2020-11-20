---
title: Elemento flag Command | Microsoft Docs
description: L'elemento del flag di comando modifica il relativo elemento padre. Esaminare gli elementi padre e gli elementi figlio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15dbf960aebc543b71ff282e525476583bdeba3d
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974189"
---
# <a name="command-flag-eelement"></a>Flag di comando Eelement
Modifica il relativo elemento padre.

## <a name="syntax"></a>Sintassi

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nella sezione seguente vengono descritti i valori degli elementi validi.

### <a name="attributes"></a>Attributi
 No.

### <a name="child-elements"></a>Elementi figlio

|Valore|Description|
|-----------|-----------------|
|AllowParams|Indica che gli utenti possono immettere i parametri del comando nella finestra di **comando** quando digitano il nome canonico del comando.<br /><br /> Valido per: `Button`|
|AlwaysCreate|Il menu viene creato anche se non contiene gruppi o pulsanti.<br /><br /> Valido per: `Menu`|
|CaseSensitive|Le voci utente fanno distinzione tra maiuscole e minuscole.<br /><br /> Valido per: `Combo`|
|CommandWellOnly|Applicare questo flag se il comando non viene visualizzato nel menu di primo livello e si desidera renderlo disponibile per la personalizzazione della shell aggiuntiva, ad esempio per associarlo a un tasto di scelta rapida. Dopo aver installato il pacchetto VSPackage, è possibile personalizzare questi comandi aprendo la finestra di dialogo **Opzioni** e quindi modificando il posizionamento dei comandi nella categoria **ambiente tastiera** . Questo flag non influisce sulla selezione host nei menu di scelta rapida, nelle barre degli strumenti, nei controller di menu o nei sottomenu.<br /><br /> Valido per: `Button` , `Combo`|
|DefaultDisabled|Per impostazione predefinita, il comando viene disabilitato se il pacchetto VSPackage che lo implementa non viene caricato o se il `QueryStatus` metodo non è stato chiamato.<br /><br /> Valido per: `Button` , `Combo`|
|DefaultDocked|Ancorato per impostazione predefinita. Questa impostazione non si applica più alle barre degli strumenti perché sono sempre ancorate.|
|DefaultInvisible|Per impostazione predefinita, il comando è invisibile se il pacchetto VSPackage che lo implementa non viene caricato o se il `QueryStatus` metodo non è stato chiamato.<br /><br /> Si consiglia di combinare questo oggetto con il `DynamicVisibility` flag.<br /><br /> Valido per: `Button` , `Combo` , `Menu`|
|DontCache|L'ambiente di sviluppo non memorizza nella cache i `QueryStatus` risultati del metodo per questo comando.<br /><br /> Per un menu, questo indica a un controller di menu di non memorizzare nella cache il testo delle voci di menu. Utilizzare questo flag quando il menu contiene elementi dinamici o elementi con testo dinamico.<br /><br /> Valido per: `Button` , `Menu`|
|DynamicItemStart|Indica l'inizio di un elenco dinamico. Ciò consente all'ambiente di compilare un elenco chiamando successivamente il `QueryStatus` Metodo sugli elementi dell'elenco fino a quando non viene restituito il flag di OLECMDERR_E_UNSUPPORTED. Questa operazione è valida per elementi come gli elenchi degli ultimi elementi usati (MRU) e gli elenchi di finestre.<br /><br /> Valido per: `Button`|
|DynamicVisibility|La visibilità del comando può essere modificata tramite il `QueryStatus` metodo o tramite un GUID di contesto incluso nella `VisibilityConstraints` sezione.<br /><br /> Si applica ai comandi visualizzati nei menu e nelle barre degli strumenti della finestra degli strumenti, ma non nelle barre degli strumenti di primo livello visualizzate nella finestra principale. Gli elementi della barra degli strumenti di primo livello possono essere disabilitati, ma non nascosti, quando viene restituito il flag OLECMDF_INVISIBLE dal `QueryStatus` metodo. I comandi della barra degli strumenti che vengono visualizzati nelle barre degli strumenti della finestra degli strumenti possono essere nascosti.<br /><br /> In un menu questo flag indica anche che deve essere nascosto automaticamente quando tutti i relativi membri sono nascosti. Questo flag viene in genere assegnato ai sottomenu perché i menu di primo livello dispongono già di questo comportamento.<br /><br /> Questo flag deve essere combinato con il `DefaultInvisible` flag.<br /><br /> Valido per: `Button` , `Combo` , `Menu`|
|Filtro tasti|Vedere l'argomento relativo alle chiavi di filtro in [elemento combinato](../extensibility/combo-element.md).<br /><br /> Valido per: `Combo`|
|FixMenuController|Se questo comando è posizionato in un controller di menu, il comando è sempre il valore predefinito. ovvero, il comando viene selezionato ogni volta che viene selezionato il pulsante del controller di menu. Se per il controller di menu è `TextIsAnchorCommand` impostato il flag, il controller di menu accetta anche il testo del comando con il `FixMenuController` flag.<br /><br /> Un solo comando in un controller di menu deve avere il `FixMenuController` flag. Se più di un comando è così contrassegnato, l'ultimo comando nel menu diventa il comando predefinito.<br /><br /> Valido per: `Button`|
|IconAndText|Mostra un'icona e un testo nel menu e nella barra degli strumenti.<br /><br /> Valido per: `Button` , `Combo` , `Menu`|
|NoAutoComplete|La funzionalità di completamento automatico è disabilitata.<br /><br /> Valido per: `Combo`|
|NoButtonCustomize|Non consentire all'utente di personalizzare questo pulsante.<br /><br /> Valido per: `Button` , `Combo`|
|NoKeyCustomize|Non abilitare la personalizzazione della tastiera.<br /><br /> Valido per: `Button` , `Combo`|
|NoShowOnMenuController|Se questo comando è posizionato in un controller di menu, il comando non viene visualizzato nell'elenco a discesa.<br /><br /> Valido per: `Button`|
|NotInTBList|Non viene visualizzato nell'elenco delle barre degli strumenti disponibili. Questa operazione è valida solo per i tipi di menu della barra degli strumenti.<br /><br /> Valido per: `Menu`|
|NoToolbarClose|L'utente non può chiudere la barra degli strumenti. Questa operazione è valida solo per i tipi di menu della barra degli strumenti.<br /><br /> Valido per: `Menu`|
|PICT|Mostra solo un'icona su una barra degli strumenti, ma solo il testo di un menu. Se non viene specificata alcuna icona, Mostra uno spazio vuoto selezionabile su una barra degli strumenti.<br /><br /> Valido per: `Button`|
|Postexec|Rende il comando non bloccante. L'ambiente di sviluppo rinvia l'esecuzione fino a quando non vengono completate tutte le query di pre-elaborazione.<br /><br /> Valido per: `Button`|
|RouteToDocs|Il comando viene indirizzato al documento attivo.<br /><br /> Valido per: `Button`|
|StretchHorizontally|Quando questo flag è impostato, la larghezza diventa la larghezza minima della casella combinata e, se è presente spazio sulla barra degli strumenti, la casella combinata si estende per riempire lo spazio disponibile. Questa situazione si verifica solo se la barra degli strumenti è ancorata orizzontalmente e solo una casella combinata sulla barra degli strumenti può utilizzare il flag (il flag viene ignorato su tutti tranne la prima casella combinata).<br /><br /> Valido per: `Combo`|
|TEXTCHANGES al|Il testo del comando o del menu può essere modificato in fase di esecuzione, in genere tramite il `QueryStatus` metodo.<br /><br /> Valido per: `Button` , `Menu`|
|TextChangesButton|Valido per: `Button`|
|TextIsAnchorCommand|Per un controller di menu, il testo del menu viene tratto dal comando predefinito (ancoraggio). Un comando di ancoraggio è l'ultimo comando selezionato o bloccato. Se questo flag non è impostato, il controller di menu usa il proprio `MenuText` campo. Tuttavia, se si fa clic sul controller dei menu, viene ancora abilitato l'ultimo comando selezionato da tale controller.<br /><br /> Si consiglia di combinare questo flag con il `TextChanges` flag.<br /><br /> Questo flag si applica solo ai menu di tipo MenuController o MenuControllerLatched.<br /><br /> Valido per: `Menu`|
|TextMenuCtrlUseMenu|Usare il `MenuText` campo nei controller di menu. Il campo predefinito è `ButtonText` .<br /><br /> Valido per: `Button`|
|TextMenuUseButton|Usare il `ButtonText` campo per i menu. Il campo predefinito è `MenuText` se è specificato.<br /><br /> Valido per: `Button`|
|TextOnly|Mostra solo il testo su una barra degli strumenti o un menu, ma nessuna icona anche se l'icona è specificata.<br /><br /> Valido per: `Button`|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Fornisce un gruppo per gli elementi [elemento del pulsante](../extensibility/button-element.md) .|
|[Menu (elemento)](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un VSPackage.|

## <a name="see-also"></a>Vedere anche
- [Tabella comandi di Visual Studio (. File vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
