---
title: Elemento Flag di comando Documenti Microsoft
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
ms.openlocfilehash: 84138a69dbb42fc349c12276fd7cca4b593e4d47
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649373"
---
# <a name="command-flag-eelement"></a>Flag di comando Eelement
Modifica l'elemento padre.

## <a name="syntax"></a>Sintassi

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nella sezione seguente vengono descritti i valori validi degli elementi.

### <a name="attributes"></a>Attributes
 No.

### <a name="child-elements"></a>Elementi figlio

|valore|Descrizione|
|-----------|-----------------|
|AllowParams|Indica che gli utenti possono immettere parametri di comando nella finestra di **comando** quando digitano il nome canonico del comando.<br /><br /> Valido per:`Button`|
|AlwaysCreate (Crea always)|Il menu viene creato anche se non ha gruppi o pulsanti.<br /><br /> Valido per:`Menu`|
|CaseSensitive|Per le voci utente viene fatta distinzione tra maiuscole e minuscole.<br /><br /> Valido per:`Combo`|
|CommandWellOnly|Applicare questo flag se il comando non viene visualizzato nel menu di primo livello e si desidera renderlo disponibile per la personalizzazione aggiuntiva della shell, ad esempio per associarlo a una scelta rapida da tastiera. Dopo aver installato il pacchetto VSPackage, è possibile personalizzare questi comandi aprendo la finestra di dialogo **Opzioni** e quindi modificando la posizione dei comandi nella categoria **Ambiente tastiera.** Questo flag non influisce sul posizionamento nei menu di scelta rapida, nelle barre degli strumenti, nei controller di menu o nei sottomenu.<br /><br /> Valido per: `Button`,`Combo`|
|DefaultDisabled (Disabilitato)|Per impostazione predefinita, il comando è disabilitato se il `QueryStatus` pacchetto VSPackage che lo implementa non è caricato o il metodo non è stato chiamato.<br /><br /> Valido per: `Button`,`Combo`|
|DefaultAncorato|Ancorato per impostazione predefinita. Questa impostazione non si applica più alle barre degli strumenti perché sono sempre ancorate.|
|DefaultInvisible (invisibile all'in|Per impostazione predefinita, il comando è invisibile se `QueryStatus` il pacchetto VSPackage che lo implementa non è caricato o il metodo non è stato chiamato.<br /><br /> Si consiglia di combinare `DynamicVisibility` questo con la bandiera.<br /><br /> Valido `Button`per: `Combo`, ,`Menu`|
|Proprietà DontCache|L'ambiente di sviluppo `QueryStatus` non memorizza nella cache i risultati del metodo per questo comando.<br /><br /> Per un menu, questo indica a un controller di menu di non memorizzare nella cache il testo delle relative voci di menu. Utilizzare questo flag quando il menu contiene voci dinamiche o voci con testo dinamico.<br /><br /> Valido per: `Button`,`Menu`|
|DynamicItemStart|Indica l'inizio di un elenco dinamico. Ciò consente all'ambiente di compilare `QueryStatus` un elenco chiamando successivamente il metodo sugli elementi dell'elenco fino a quando non viene restituito il flag di OLECMDERR_E_UNSUPPORTED. Questo funziona bene per gli elementi, ad esempio gli elenchi mRU (Most Used) e gli elenchi di finestre.<br /><br /> Valido per:`Button`|
|DynamicVisibility (Visibilità dinamica)|La visibilità del comando può `QueryStatus` essere modificata tramite il `VisibilityConstraints` metodo o tramite un GUID di contesto incluso nella sezione.<br /><br /> Si applica ai comandi visualizzati nei menu e nelle barre degli strumenti della finestra degli strumenti, ma non nelle barre degli strumenti di primo livello visualizzate nella finestra principale. Gli elementi della barra degli strumenti di primo livello possono essere `QueryStatus` disabilitati ma non nascosti, quando il OLECMDF_INVISIBLE flag viene restituito dal metodo. I comandi della barra degli strumenti visualizzati sulle barre degli strumenti della finestra degli strumenti possono essere nascosti.<br /><br /> In un menu, questo flag indica anche che deve essere nascosto automaticamente quando tutti i relativi membri sono nascosti. Questo flag viene in genere assegnato ai sottomenu perché i menu di primo livello hanno già questo comportamento.<br /><br /> Questo flag deve essere `DefaultInvisible` combinato con la bandiera.<br /><br /> Valido `Button`per: `Combo`, ,`Menu`|
|FilterKeys (Tasti filtro)|Vedere l'argomento Filtro delle chiavi in [Elemento combinato](../extensibility/combo-element.md).<br /><br /> Valido per:`Combo`|
|FixMenuController|Se questo comando è posizionato su un controller di menu, il comando è sempre l'impostazione predefinita; ovvero, il comando viene selezionato ogni volta che viene selezionato il pulsante del controller di menu stesso. Se il controller `TextIsAnchorCommand` di menu ha il flag impostato, il controller `FixMenuController` di menu prende anche il testo dal comando che contiene il flag.<br /><br /> Solo un comando in un `FixMenuController` controller di menu deve avere il flag. Se più di un comando è così contrassegnato, l'ultimo comando nel menu diventa il comando predefinito.<br /><br /> Valido per:`Button`|
|IconaTesto|Visualizzare un'icona e testo nel menu e nella barra degli strumenti.<br /><br /> Valido `Button`per: `Combo`, ,`Menu`|
|NoAutoComplete|La funzione di completamento automatico è disattivata.<br /><br /> Valido per:`Combo`|
|NoButtonCustomize|Non consentire all'utente di personalizzare questo pulsante.<br /><br /> Valido per: `Button`,`Combo`|
|NoKeyPersonalizza|Non abilitare la personalizzazione della tastiera.<br /><br /> Valido per: `Button`,`Combo`|
|NoShowOnMenuController|Se questo comando è posizionato su un controller di menu, il comando non viene visualizzato nell'elenco a discesa.<br /><br /> Valido per:`Button`|
|NotInTBList (informazioni in stato di inademazione|Non viene visualizzato nell'elenco delle barre degli strumenti disponibili. Questa opzione è valida solo per i tipi di menu Barra degli strumenti.<br /><br /> Valido per:`Menu`|
|NoToolbarChiudi|L'utente non può chiudere la barra degli strumenti. Questa opzione è valida solo per i tipi di menu Barra degli strumenti.<br /><br /> Valido per:`Menu`|
|Pict|Visualizzare solo un'icona su una barra degli strumenti, ma solo il testo di un menu. Se non viene specificata alcuna icona, viene visualizzato uno spazio vuoto selezionabile su una barra degli strumenti.<br /><br /> Valido per:`Button`|
|PostExec (incarica di post-Exec|Rende il comando non bloccante. L'ambiente di sviluppo rinvia l'esecuzione fino al completamento di tutte le query di pre-elaborazione.<br /><br /> Valido per:`Button`|
|RouteToDocs|Il comando viene indirizzato al documento attivo.<br /><br /> Valido per:`Button`|
|StretchHorizontally|Quando questo flag è impostato, la larghezza diventa la larghezza minima per la casella combinata e, se c'è spazio sulla barra degli strumenti, la casella combinata si estende per riempire lo spazio disponibile. Ciò si verifica solo se la barra degli strumenti è ancorata orizzontalmente e solo una casella combinata sulla barra degli strumenti può utilizzare il flag (il flag viene ignorato su tutti tranne la prima casella combinata).<br /><br /> Valido per:`Combo`|
|Modifiche al testo|Il comando o il testo del menu può `QueryStatus` essere modificato in fase di esecuzione, in genere tramite il metodo .<br /><br /> Valido per: `Button`,`Menu`|
|Controllo TextChangesButton|Valido per:`Button`|
|TextIsAnchorCommand|Per un controller di menu, il testo del menu viene ricavato dal comando predefinito (ancoraggio). Un comando di ancoraggio è l'ultimo comando selezionato o aggrovigliato. Se questo flag non è impostato, `MenuText` il controller di menu utilizza il proprio campo. Tuttavia, facendo clic sul controller di menu viene ancora abilitato l'ultimo comando selezionato da tale controller.<br /><br /> Si consiglia di combinare questo `TextChanges` flag con il flag.<br /><br /> Questo flag si applica solo ai menu di tipo MenuController o MenuControllerLatched.<br /><br /> Valido per:`Menu`|
|TestoMenuCtrlUseMenu|Utilizzare `MenuText` il campo nei controller di menu. Il campo `ButtonText`predefinito è .<br /><br /> Valido per:`Button`|
|TextMenuUseButton|Utilizzare `ButtonText` il campo per i menu. Il campo `MenuText` predefinito è se specificato.<br /><br /> Valido per:`Button`|
|Solo testo|Mostra solo il testo di una barra degli strumenti o di un menu, ma nessuna icona anche se è specificata l'icona.<br /><br /> Valido per:`Button`|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Fornisce un gruppo per gli elementi [dell'elemento Button.](../extensibility/button-element.md)|
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un pacchetto VSPackage.|

## <a name="see-also"></a>Vedere anche
- [Tabella dei comandi di Visual Studio (. Vsct) File](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
