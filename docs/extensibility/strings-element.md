---
title: Elemento Strings | Microsoft Docs
description: L'elemento Strings contiene un elemento figlio ButtonText e altri elementi figlio facoltativi. Una e commerciale nella stringa di testo specifica un tasto di scelta rapida.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: dc5ace6f8c59b8968398bf9050100f7a2a15c155
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158203"
---
# <a name="strings-element"></a>Elemento Strings
L'elemento Strings deve contenere almeno un **elemento figlio ButtonText.** Tutti gli altri elementi figlio sono facoltativi. I caratteri XML non validi, ad esempio '&' e '<', devono essere codificati come entità (' &amp; ' e ' ' e così &lt; via).

 Una e commerciale nella stringa di testo specifica il tasto di scelta rapida per il comando.

## <a name="syntax"></a>Sintassi

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|Linguaggio|facoltativo. Language=".".|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|ButtonText|Questo campo e i cinque campi di testo seguenti in una definizione di comando consentono di specificare il testo visualizzato in vari menu. Per impostazione predefinita, il `ButtonText` campo viene visualizzato nei controller di menu. Il `ButtonText` campo diventa l'impostazione predefinita anche se gli altri campi di testo sono vuoti. Il `ButtonText` campo non può essere vuoto anche se sono specificati gli altri campi di testo.|
|Tooltiptext|Il `ToolTipText` campo specifica il testo visualizzato nella descrizione comando per una voce di menu.<br /><br /> Se il `ToolTipText` campo è vuoto, `ButtonText` viene usato il campo .|
|MenuText|Il campo specifica il testo visualizzato per un comando se si trova nel menu principale, in una barra degli strumenti, in un menu di scelta rapida o `MenuText` in un sottomenu. Se il `MenuText` campo è vuoto, l'ambiente di sviluppo integrato (IDE) usa il `ButtonText` campo . Il `MenuText` campo può essere usato anche per la localizzazione.<br /><br /> Per i menu di scelta rapida, il campo è il nome visualizzato nella barra degli strumenti Menu di scelta rapida, che consente la personalizzazione dei menu di scelta rapida `MenuText` nell'IDE. È quindi necessario assegnare un nome specifico al menu di scelta rapida. Ad esempio, usare "Menu di scelta rapida del pacchetto widget" anziché "Collegamento".<br /><br /> Se il `MenuText` campo non è specificato, viene usato il `ButtonText` campo .|
|CommandName|Il campo specifica il testo visualizzato nella categoria tastiera nella scheda Comandi della finestra di dialogo Personalizza (disponibile scegliendo Personalizza `CommandName` dal menu Strumenti).    |
|CanonicalName|Il campo Inglese specifica il nome del comando in inglese che può essere immesso nella finestra di comando `CanonicalName` per eseguire la voce di menu.  L'IDE rimuove tutti i caratteri che non sono lettere, cifre, caratteri di sottolineatura o punti incorporati. Questo testo viene quindi concatenato al `ButtonText` campo per definire il comando. Ad esempio, **New Project** nel menu **File** diventa il comando File.NewProject.<br /><br /> Se il campo Inglese non è specificato, l'IDE usa il campo e rimuove tutte le lettere, le cifre, i caratteri di sottolineatura e i `CanonicalName` `ButtonText` punti incorporati. Ad esempio, il testo del pulsante "&Definisci comandi..." diventa DefineCommands, in cui vengono rimossi la e commerciale, lo spazio e i puntini di sospensione.<br /><br /> Se il flag viene specificato e il testo del comando viene modificato, il comando corrispondente riconosciuto dalla finestra di comando non cambia, ma rimane la forma canonica dei campi originali o `TextChanges`  `ButtonText` in `CanonicalName` inglese.|
|LocCanonicalName|Il `LocCanonicalName` campo si comporta in modo identico al campo `CanonicalName` inglese, ma consente la specifica del testo del comando localizzato. È possibile specificare entrambi i campi canonici. Poiché l'IDE analizza solo  il testo immesso nella finestra di comando e lo associa a un comando, il testo in inglese e non inglese può essere associato allo stesso comando.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Button](../extensibility/button-element.md)|Definisce un elemento con cui l'utente può interagire.|
|[Elemento Menu](../extensibility/menu-element.md)|Definisce una singola voce di menu.|
|[Elemento Combo](../extensibility/combo-element.md)|Definisce i comandi visualizzati in una casella combinata.|

## <a name="see-also"></a>Vedi anche
- [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
