---
title: Comando elemento Commandflag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a38708d6256556693b7ab1dfc8c04b79f484ee8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334843"
---
# <a name="command-flag-eelement"></a>Flag di comando Eelement
Modifica il relativo elemento padre.

## <a name="syntax"></a>Sintassi

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 La sezione seguente descrive i valori di elemento valido.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Value|Descrizione|
|-----------|-----------------|
|AllowParams|Indica che gli utenti possono immettere i parametri di comando in di **comando** finestra quando l'utente digita il nome canonico del comando.<br /><br /> Valido per: `Button`|
|AlwaysCreate|Menu viene creato anche se non contiene né gruppi di pulsanti.<br /><br /> Valido per: `Menu`|
|CaseSensitive|Le voci di utente sono tra maiuscole e minuscole.<br /><br /> Valido per: `Combo`|
|CommandWellOnly|Applicare questo flag se il comando non viene visualizzato nel menu di primo livello e si vuole renderlo disponibile per la personalizzazione di altre shell, ad esempio, per associarla a un tasto di scelta rapida. Dopo aver installato il pacchetto VSPackage, è possibile personalizzare questi comandi, aprire il **opzioni** nella finestra di dialogo e quindi modificando il posizionamento del comando sotto il **tastiera ambiente** categoria. Questo flag non influenza la selezione host nei menu di scelta rapida, barre degli strumenti, i controller di menu o sottomenu.<br /><br /> Valida per: `Button`, `Combo`|
|DefaultDisabled|Per impostazione predefinita, il comando è disabilitato se non viene caricato il pacchetto VSPackage che lo implementa o `QueryStatus` (metodo) non è stato chiamato.<br /><br /> Valida per: `Button`, `Combo`|
|DefaultDocked|Ancorato per impostazione predefinita. Questa impostazione non è più applicabile alle barre degli strumenti perché sono sempre sono ancorate.|
|DefaultInvisible|Per impostazione predefinita, il comando è invisibile se non viene caricato il pacchetto VSPackage che lo implementa o `QueryStatus` (metodo) non è stato chiamato.<br /><br /> È consigliabile che si combina con i `DynamicVisibility` flag.<br /><br /> Valida per: `Button`, `Combo`, `Menu`|
|DontCache|L'ambiente di sviluppo non memorizza nella cache il `QueryStatus` i risultati dei metodi per questo comando.<br /><br /> Per un menu, indica a un controller di menu non memorizzare nella cache il testo relativo delle voci di menu. Usare questo flag quando il menu contiene gli elementi dinamici o elementi che contengono il testo dinamico.<br /><br /> Valida per: `Button`, `Menu`|
|DynamicItemStart|Indica l'inizio di un elenco dinamico. In questo modo l'ambiente compilare un elenco chiamando in successione i `QueryStatus` metodo sugli elementi dell'elenco finché non viene restituito il flag OLECMDERR_E_UNSUPPORTED. Ciò vale per gli elementi, ad esempio utilizzati più di recente (MRU) gli elenchi e finestra.<br /><br /> Valido per: `Button`|
|DynamicVisibility|La visibilità del comando può essere modificata tramite il `QueryStatus` (metodo) o tramite un GUID che viene incluso nel contesto di `VisibilityConstraints` sezione.<br /><br /> Si applica ai comandi che vengono visualizzati nei menu e barre degli strumenti finestra degli strumenti, ma non sulle barre degli strumenti di livello superiore che vengono visualizzati nella finestra principale. Gli elementi di primo livello sulla barra degli strumenti possono essere disabilitati, ma non nascosti, quando viene restituito il flag OLECMDF_INVISIBLE dal `QueryStatus` (metodo). Comandi della barra degli strumenti che vengono visualizzati nelle barre degli strumenti finestra degli strumenti possono essere nascosti.<br /><br /> In un menu, questo flag indica anche che si deve essere automaticamente nascosto quando tutti i relativi membri sono nascosti. Questo flag viene in genere assegnato al sottomenu poiché i menu di primo livello è già installato questo comportamento.<br /><br /> Questo flag deve essere combinato con il `DefaultInvisible` flag.<br /><br /> Valida per: `Button`, `Combo`, `Menu`|
|FilterKeys|Vedere l'argomento di filtro chiavi sotto [elemento Combo](../extensibility/combo-element.md).<br /><br /> Valido per: `Combo`|
|FixMenuController|Se questo comando viene posizionato su un controller di menu, il comando è sempre il valore predefinito; il comando è selezionato, ovvero ogni volta che si seleziona il pulsante di menu controller stesso. Se il controller di menu ha il `TextIsAnchorCommand` flag impostato, quindi il controller di menu Usa anche il testo del comando che ha la `FixMenuController` flag.<br /><br /> Deve avere un solo comando in un controller di menu il `FixMenuController` flag. Se più di un comando viene pertanto contrassegnato, l'ultimo comando nel menu di scelta diventa il comando predefinito.<br /><br /> Valido per: `Button`|
|IconAndText|Mostra un'icona e testo nel menu e barra degli strumenti.<br /><br /> Valida per: `Button`, `Combo`, `Menu`|
|NoAutoComplete|Funzionalità di completamento automatico è disabilitato.<br /><br /> Valido per: `Combo`|
|NoButtonCustomize|Non consentire all'utente di personalizzare questo pulsante.<br /><br /> Valida per: `Button`, `Combo`|
|NoKeyCustomize|Non abilitare la personalizzazione della tastiera.<br /><br /> Valida per: `Button`, `Combo`|
|NoShowOnMenuController|Se questo comando viene posizionato su un controller di menu, il comando non viene visualizzato nell'elenco a discesa.<br /><br /> Valido per: `Button`|
|NotInTBList|Non viene visualizzato nell'elenco delle barre degli strumenti disponibili. Ciò è valido solo per i tipi di menu della barra degli strumenti.<br /><br /> Valido per: `Menu`|
|NoToolbarClose|L'utente non è possibile chiudere la barra degli strumenti. Ciò è valido solo per i tipi di menu della barra degli strumenti.<br /><br /> Valido per: `Menu`|
|PICT|Mostra solo un'icona su una barra degli strumenti, ma solo il testo in un menu. Se non viene specificata alcuna icona, viene illustrato uno spazio vuoto selezionabile in una barra degli strumenti.<br /><br /> Valido per: `Button`|
|PostExec|Esegue il comando non bloccante. L'ambiente di sviluppo rinvia l'esecuzione fino al completamento di tutte le query pre-elaborazione.<br /><br /> Valido per: `Button`|
|RouteToDocs|Il comando viene instradato al documento attivo.<br /><br /> Valido per: `Button`|
|StretchHorizontally|Quando questo flag è impostato, la larghezza diventa la larghezza minima per la casella combinata e se c'è spazio sulla barra degli strumenti, la casella combinata si estende fino a riempire lo spazio disponibile. Ciò si verifica solo se la barra degli strumenti è ancorato in orizzontale e solo una casella combinata nella barra degli strumenti è possibile usare il flag (il flag viene ignorato in tutto eccetto la prima casella combinata).<br /><br /> Valido per: `Combo`|
|TextMenuUseButton|Usare il `ButtonText` campo per i menu. Il campo predefinito è `MenuText` se è specificato.<br /><br /> Valido per: `Button`|
|TextChanges|Il testo di comando o un menu può essere modificato in fase di esecuzione, in genere tramite il `QueryStatus` (metodo).<br /><br /> Valida per: `Button`, `Menu`|
|TextChangesButton|Valido per: `Button`|
|TextIsAnchorCommand|Per un controller di menu, viene acquisito il testo del menu del comando predefinito (ancoraggio). Un comando di ancoraggio è l'ultimo comando selezionato o impostare un latch. Se questo flag non è impostato, il controller di menu Usa il proprio `MenuText` campo. Tuttavia, facendo clic su controller di menu consente ancora l'ultimo comando selezionato dal controller di.<br /><br /> È consigliabile che si combina questo flag con la `TextChanges` flag.<br /><br /> Questo flag si applica solo ai menu di tipo MenuController o MenuControllerLatched.<br /><br /> Valido per: `Menu`|
|TextMenuCtrlUseMenu|Usare il `MenuText` campo nei controller di menu. Il campo predefinito è `ButtonText`.<br /><br /> Valido per: `Button`|
|TextMenuUseButton|Usare il `ButtonText` campo per i menu. Il campo predefinito è `MenuText` se è specificato.<br /><br /> Valido per: `Button`|
|TextOnly|Mostrare solo testo in una barra degli strumenti o un menu, ma nessuna icona anche se viene specificato l'icona.<br /><br /> Valido per: `Button`|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Fornisce un gruppo per [elemento pulsante](../extensibility/button-element.md) elementi.|
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un pacchetto VSPackage.|

## <a name="see-also"></a>Vedere anche
- [Tabella di comandi Visual Studio (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)