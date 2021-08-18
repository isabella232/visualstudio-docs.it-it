---
title: Elemento flag di comando | Microsoft Docs
description: L'elemento flag Command modifica l'elemento padre. Esaminare gli elementi padre e gli elementi figlio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1be87038e7baedaac0ea1244b8acfc500c70a2c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111970"
---
# <a name="command-flag-eelement"></a>Flag di comando Eelement
Modifica l'elemento padre.

## <a name="syntax"></a>Sintassi

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nella sezione seguente vengono descritti i valori degli elementi validi.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Valore|Descrizione|
|-----------|-----------------|
|AllowParams|Indica che gli utenti possono immettere parametri di comando nella finestra **di** comando quando digitano il nome canonico del comando.<br /><br /> Valido per: `Button`|
|AlwaysCreate|Il menu viene creato anche se non ha gruppi o pulsanti.<br /><br /> Valido per: `Menu`|
|CaseSensitive|Per le voci utente viene fatto distinzione tra maiuscole e minuscole.<br /><br /> Valido per: `Combo`|
|CommandWellOnly|Applicare questo flag se il comando non viene visualizzato nel menu di primo livello e si vuole renderlo disponibile per la personalizzazione aggiuntiva della shell, ad esempio per associarlo a un tasto di scelta rapida. Dopo aver installato il pacchetto VSPackage, è  possibile personalizzare questi comandi aprendo la finestra di dialogo Opzioni e quindi modificando il posizionamento dei comandi nella **categoria Ambiente tastiera.** Questo flag non influisce sulla posizione in menu di scelta rapida, barre degli strumenti, controller di menu o sottomenu.<br /><br /> Valido per: `Button` , `Combo`|
|DefaultDisabled|Per impostazione predefinita, il comando è disabilitato se il pacchetto VSPackage che lo implementa non viene caricato o il `QueryStatus` metodo non è stato chiamato.<br /><br /> Valido per: `Button` , `Combo`|
|DefaultDocked|Ancorato per impostazione predefinita. Questa impostazione non si applica più alle barre degli strumenti perché sono sempre ancorate.|
|DefaultInvisible|Per impostazione predefinita, il comando è invisibile se il pacchetto VSPackage che lo implementa non viene caricato o il `QueryStatus` metodo non è stato chiamato.<br /><br /> È consigliabile combinarlo con il `DynamicVisibility` flag .<br /><br /> Valido per: `Button` , `Combo` , `Menu`|
|DontCache|L'ambiente di sviluppo non memorizza nella cache `QueryStatus` i risultati del metodo per questo comando.<br /><br /> Per un menu, indica a un controller di menu di non memorizzare nella cache il testo delle relative voci di menu. Usare questo flag quando il menu contiene elementi dinamici o elementi con testo dinamico.<br /><br /> Valido per: `Button` , `Menu`|
|DynamicItemStart|Indica l'inizio di un elenco dinamico. In questo modo l'ambiente può compilare un elenco chiamando successivamente il metodo sugli elementi dell'elenco fino a quando non viene restituito `QueryStatus` OLECMDERR_E_UNSUPPORTED flag . Ciò funziona bene per gli elementi, ad esempio gli elenchi MRU (Most Recently Used) e gli elenchi di finestre.<br /><br /> Valido per: `Button`|
|DynamicVisibility|La visibilità del comando può essere modificata tramite il metodo o tramite un GUID di contesto `QueryStatus` incluso nella `VisibilityConstraints` sezione .<br /><br /> Si applica ai comandi visualizzati nei menu e nelle barre degli strumenti delle finestre degli strumenti, ma non nelle barre degli strumenti di primo livello visualizzate nella finestra principale. Gli elementi della barra degli strumenti di primo livello possono essere disabilitati ma non nascosti, quando il flag OLECMDF_INVISIBLE viene restituito dal `QueryStatus` metodo . I comandi della barra degli strumenti visualizzati sulle barre degli strumenti della finestra degli strumenti possono essere nascosti.<br /><br /> In un menu, questo flag indica anche che deve essere automaticamente nascosto quando tutti i relativi membri sono nascosti. Questo flag viene in genere assegnato ai sottomenu perché i menu di primo livello hanno già questo comportamento.<br /><br /> Questo flag deve essere combinato con il `DefaultInvisible` flag .<br /><br /> Valido per: `Button` , `Combo` , `Menu`|
|FilterKeys|Vedere l'argomento Filtro delle chiavi in [Elemento combinato](../extensibility/combo-element.md).<br /><br /> Valido per: `Combo`|
|FixMenuController|Se questo comando è posizionato in un controller di menu, il comando è sempre l'impostazione predefinita. in altri, il comando viene selezionato ogni volta che viene selezionato il pulsante del controller di menu stesso. Se il controller di menu ha il flag impostato, il controller di menu prende anche il testo dal `TextIsAnchorCommand` comando che ha il flag `FixMenuController` .<br /><br /> Il flag deve essere impostato su un solo comando in un controller `FixMenuController` di menu. Se più comandi sono contrassegnati, l'ultimo comando nel menu diventa il comando predefinito.<br /><br /> Valido per: `Button`|
|IconAndText|Visualizzare un'icona e un testo nel menu e nella barra degli strumenti.<br /><br /> Valido per: `Button` , `Combo` , `Menu`|
|NoAutoComplete|La funzionalità completamento automatico è disabilitata.<br /><br /> Valido per: `Combo`|
|NoButtonCustomize|Non consentire all'utente di personalizzare questo pulsante.<br /><br /> Valido per: `Button` , `Combo`|
|NoKeyCustomize|Non abilitare la personalizzazione della tastiera.<br /><br /> Valido per: `Button` , `Combo`|
|NoShowOnMenuController|Se questo comando è posizionato in un controller di menu, il comando non viene visualizzato nell'elenco a discesa.<br /><br /> Valido per: `Button`|
|NotInTBList|Non viene visualizzato nell'elenco delle barre degli strumenti disponibili. Questa opzione è valida solo per i tipi di menu della barra degli strumenti.<br /><br /> Valido per: `Menu`|
|NoToolbarClose|L'utente non può chiudere la barra degli strumenti. Questa opzione è valida solo per i tipi di menu della barra degli strumenti.<br /><br /> Valido per: `Menu`|
|Pict|Mostra solo un'icona su una barra degli strumenti, ma solo il testo in un menu. Se non viene specificata alcuna icona, visualizza uno spazio vuoto selezionabile su una barra degli strumenti.<br /><br /> Valido per: `Button`|
|PostExec|Rende il comando non bloccante. L'ambiente di sviluppo rinvia l'esecuzione fino al completamento di tutte le query di pre-elaborazione.<br /><br /> Valido per: `Button`|
|RouteToDocs|Il comando viene instradato al documento attivo.<br /><br /> Valido per: `Button`|
|StretchHorizontally|Quando questo flag è impostato, la larghezza diventa la larghezza minima per la casella combinata e, se c'è spazio sulla barra degli strumenti, la casella combinata si estende per riempire lo spazio disponibile. Questo errore si verifica solo se la barra degli strumenti è ancorata orizzontalmente e solo una casella combinata sulla barra degli strumenti può usare il flag (il flag viene ignorato in tutte le caselle tranne la prima).<br /><br /> Valido per: `Combo`|
|Modifiche di testo|Il testo del comando o del menu può essere modificato in fase di esecuzione, in genere tramite il `QueryStatus` metodo .<br /><br /> Valido per: `Button` , `Menu`|
|Controllo TextChangesButton|Valido per: `Button`|
|TextIsAnchorCommand|Per un controller di menu, il testo del menu viene tratto dal comando predefinito (ancoraggio). Un comando di ancoraggio è l'ultimo comando selezionato o con latch. Se questo flag non è impostato, il controller di menu usa il proprio `MenuText` campo. Tuttavia, facendo clic sul controller di menu viene comunque abilitata l'ultimo comando selezionato da tale controller.<br /><br /> È consigliabile combinare questo flag con il `TextChanges` flag .<br /><br /> Questo flag si applica solo ai menu di tipo MenuController o MenuControllerLatched.<br /><br /> Valido per: `Menu`|
|TextMenuCtrlUseMenu|Usare il `MenuText` campo nei controller di menu. Il campo predefinito è `ButtonText` .<br /><br /> Valido per: `Button`|
|TextMenuUseButton|Usare il `ButtonText` campo per i menu. Il campo predefinito è `MenuText` se specificato.<br /><br /> Valido per: `Button`|
|TextOnly|Mostra solo il testo su una barra degli strumenti o un menu, ma nessuna icona anche se l'icona è specificata.<br /><br /> Valido per: `Button`|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Fornisce un gruppo per gli [elementi elemento](../extensibility/button-element.md) Button.|
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un VSPackage.|

## <a name="see-also"></a>Vedi anche
- [Visual Studio tabella dei comandi (. Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
