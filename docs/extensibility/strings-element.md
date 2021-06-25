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
ms.workload:
- vssdk
ms.openlocfilehash: 27a649c7d3a8bb808153c280921d2304de59c379
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899407"
---
# <a name="strings-element"></a>Elemento Strings
L'elemento Strings deve contenere almeno un **elemento figlio ButtonText.** Tutti gli altri elementi figlio sono facoltativi. I caratteri XML non validi, ad esempio '&' e '<' devono essere codificati come entità (' &amp; e ' ' ' e così &lt; via).

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
|ButtonText|Questo campo e i cinque campi di testo seguenti in una definizione di comando consentono di specificare il testo visualizzato in vari menu. Per impostazione predefinita, il `ButtonText` campo viene visualizzato nei controller di menu. Il `ButtonText` campo diventa anche l'impostazione predefinita se gli altri campi di testo sono vuoti. Il `ButtonText` campo non può essere vuoto anche se vengono specificati gli altri campi di testo.|
|Tooltiptext|Il `ToolTipText` campo specifica il testo visualizzato nella descrizione comando per una voce di menu.<br /><br /> Se il `ToolTipText` campo è vuoto, `ButtonText` viene usato il campo .|
|MenuText|Il campo specifica il testo visualizzato per un comando se si trova nel menu principale, in una barra degli strumenti, in un menu di scelta rapida o `MenuText` in un sottomenu. Se il `MenuText` campo è vuoto, l'ambiente di sviluppo integrato (IDE) usa il `ButtonText` campo . Il `MenuText` campo può essere usato anche per la localizzazione.<br /><br /> Per i menu di scelta rapida, il campo è il nome visualizzato nella barra degli strumenti menu di scelta rapida, che consente la personalizzazione dei menu di scelta rapida `MenuText` nell'IDE. Di conseguenza, è necessario essere specifici nel menu di scelta rapida. Ad esempio, usare "Menu di scelta rapida del pacchetto Widget" anziché "Collegamento".<br /><br /> Se il `MenuText` campo non viene specificato, viene usato il `ButtonText` campo .|
|CommandName|Il campo specifica il testo visualizzato nella categoria tastiera nella scheda Comandi della finestra di dialogo Personalizza (disponibile scegliendo Personalizza `CommandName` dal menu Strumenti).    |
|CanonicalName|Il campo Inglese specifica il nome del comando in testo inglese che può essere immesso nella finestra di `CanonicalName` comando per eseguire la voce di menu.  L'IDE rimuove tutti i caratteri che non sono lettere, cifre, caratteri di sottolineatura o punti incorporati. Questo testo viene quindi concatenato al `ButtonText` campo per definire il comando. Ad esempio, **Nuovo progetto** nel menu **File** diventa il comando File.NuovoProgetto.<br /><br /> Se il campo Inglese non viene specificato, l'IDE usa il campo e rimuove tutte le lettere, le cifre, i caratteri di sottolineatura `CanonicalName` `ButtonText` e i periodi incorporati. Ad esempio, il testo del pulsante "&comandi..." diventa DefineCommands, in cui vengono rimossi la e commerciale, lo spazio e i puntini di sospensione.<br /><br /> Se il flag viene specificato e il testo del comando viene modificato, il comando corrispondente riconosciuto dalla finestra di comando non cambia; rimane la forma canonica dei campi originali o `TextChanges`  `ButtonText` `CanonicalName` inglesi.|
|LocCanonicalName|Il campo si comporta in modo identico al campo inglese, ma consente di impostare il testo `LocCanonicalName` `CanonicalName` localizzato del comando. È possibile specificare entrambi i campi canonici. Poiché l'IDE analizza solo  il testo immesso nella finestra di comando e lo associa a un comando, è possibile associare allo stesso comando sia testo in inglese che non in inglese.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Button](../extensibility/button-element.md)|Definisce un elemento con cui l'utente può interagire.|
|[Elemento Menu](../extensibility/menu-element.md)|Definisce una singola voce di menu.|
|[Elemento Combo](../extensibility/combo-element.md)|Definisce i comandi visualizzati in una casella combinata.|

## <a name="see-also"></a>Vedere anche
- [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
