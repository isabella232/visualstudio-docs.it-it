---
title: Elemento Strings . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699727"
---
# <a name="strings-element"></a>Elemento Strings
L'elemento Strings deve contenere almeno un elemento figlio **ButtonText.** Tutti gli altri elementi figlio sono facoltativi. I caratteri XML non validi, ad esempio '&' e&amp;'<'&lt;devono essere codificati come entità (' e ' ' e così via).

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
|Linguaggio|Facoltativa. Lingua".".|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|TestoPulsante|Questo campo e i cinque campi di testo seguenti in una definizione di comando consentono di specificare il testo visualizzato nei vari menu. Per impostazione `ButtonText` predefinita, il campo viene visualizzato nei controller di menu. Il `ButtonText` campo diventa anche quello predefinito se gli altri campi di testo sono vuoti. Il `ButtonText` campo non può essere vuoto anche se sono specificati gli altri campi di testo.|
|Tooltiptext|Il `ToolTipText` campo specifica il testo visualizzato nella descrizione comando per una voce di menu.<br /><br /> Se `ToolTipText` il campo è `ButtonText` vuoto, viene utilizzato il campo.|
|MenuTesto|Il `MenuText` campo specifica il testo visualizzato per un comando se si trova nel menu principale, una barra degli strumenti, in un menu di scelta rapida o in un sottomenu. Se `MenuText` il campo è vuoto, l'ambiente di `ButtonText` sviluppo integrato (IDE) utilizza il campo. Il `MenuText` campo può essere utilizzato anche per la localizzazione.<br /><br /> Per i menu `MenuText` di scelta rapida, il campo è il nome visualizzato nella barra degli strumenti Menu di scelta rapida, che consente la personalizzazione dei menu di scelta rapida nell'IDE. Pertanto, essere specifici in ciò che si denomina il menu di scelta rapida; ad esempio, utilizzare "Widget Package Shortcut Menu" invece di "Shortcut".<br /><br /> Se `MenuText` il campo non `ButtonText` è specificato, viene utilizzato il campo.|
|CommandName|Il `CommandName` campo specifica il testo visualizzato nella categoria della tastiera nella scheda **Comandi** della finestra di dialogo **Personalizza** (disponibile scegliendo **Personalizza** dal menu **Strumenti).**|
|Nome canonico|Il `CanonicalName` campo Inglese specifica il nome del comando in testo inglese che può essere immesso nella finestra **di comando** per eseguire la voce di menu. L'IDE rimuove tutti i caratteri che non sono lettere, cifre, caratteri di sottolineatura o punti incorporati. Questo testo viene quindi concatenato al `ButtonText` campo per definire il comando. Ad esempio, **Nuovo progetto** nel menu **File** diventa il comando File.NewProject.<br /><br /> Se il `CanonicalName` campo inglese non è specificato, l'IDE utilizza il `ButtonText` campo e rimuove tutti tranne lettere, cifre, caratteri di sottolineatura e punti incorporati. Ad esempio, il testo del pulsante "&Definisci comandi..." diventa DefineCommands, dove vengono rimossi la e commerciale, lo spazio e i solchi.<br /><br /> Se `TextChanges` viene specificato il flag e il testo del comando viene modificato, il comando corrispondente riconosciuto dalla finestra **di comando** non cambia; rimane la forma canonica `ButtonText` dei `CanonicalName` campi originali o inglesi.|
|LocCanonicalName|Il `LocCanonicalName` campo si comporta in `CanonicalName` modo identico al campo inglese, ma consente di specificare il testo del comando localizzato. È possibile specificare entrambi i campi canonici. Poiché l'IDE analizza solo il testo immesso nella finestra di **comando** e lo associa a un comando, testo inglese e non inglese può essere associato allo stesso comando.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Button](../extensibility/button-element.md)|Definisce un elemento con cui l'utente può interagire.|
|[Elemento Menu](../extensibility/menu-element.md)|Definisce una singola voce di menu.|
|[Elemento Combo](../extensibility/combo-element.md)|Definisce i comandi visualizzati in una casella combinata.|

## <a name="see-also"></a>Vedere anche
- [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
