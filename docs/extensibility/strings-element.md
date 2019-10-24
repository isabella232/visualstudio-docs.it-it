---
title: Elemento Strings | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c91a8ea07daee77855017d641a569a892612c3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719438"
---
# <a name="strings-element"></a>Elemento Strings
L'elemento Strings deve contenere almeno un elemento figlio **ButtonText** . Tutti gli altri elementi figlio sono facoltativi. I caratteri XML non validi, ad esempio ' &' è <', devono essere codificati come entità (' &amp;' è &lt;' e così via).

 Una e commerciale nella stringa di testo specifica la scelta rapida da tastiera per il comando.

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
|language|Parametro facoltativo. Language = ".".|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|ButtonText|Questo campo e i cinque campi di testo seguenti in una definizione di comando consentono di specificare il testo visualizzato in vari menu. Per impostazione predefinita, il campo `ButtonText` viene visualizzato nei controller di menu. Se gli altri campi di testo sono vuoti, il campo `ButtonText` diventa anche il valore predefinito. Il campo `ButtonText` non può essere vuoto anche se gli altri campi di testo sono specificati.|
|ToolTipText|Il campo `ToolTipText` specifica il testo visualizzato nella descrizione comando per una voce di menu.<br /><br /> Se il campo `ToolTipText` è vuoto, viene utilizzato il campo `ButtonText`.|
|MenuText|Il campo `MenuText` specifica il testo visualizzato per un comando se si trova nel menu principale, in una barra degli strumenti, in un menu di scelta rapida o in un sottomenu. Se il campo `MenuText` è vuoto, il Integrated Development Environment (IDE) usa il campo `ButtonText`. Il campo `MenuText` può essere utilizzato anche per la localizzazione.<br /><br /> Per i menu di scelta rapida, il campo `MenuText` è il nome visualizzato nella barra degli strumenti dei menu di scelta rapida, che consente di personalizzare i menu di scelta rapida nell'IDE. Pertanto, è necessario specificare il nome del menu di scelta rapida. ad esempio, usare "menu di scelta rapida del pacchetto widget" invece di "collegamento".<br /><br /> Se il campo `MenuText` non è specificato, viene utilizzato il campo `ButtonText`.|
|CommandName|Il campo `CommandName` specifica il testo visualizzato nella categoria tastiera nella scheda **comandi** della finestra di dialogo **Personalizza** , disponibile scegliendo **Personalizza** dal menu **strumenti** .|
|CanonicalName|Il campo English `CanonicalName` specifica il nome del comando nel testo in lingua inglese che può essere immesso nella finestra di **comando** per eseguire la voce di menu. L'IDE rimuove tutti i caratteri che non sono lettere, cifre, caratteri di sottolineatura o punti incorporati. Questo testo viene quindi concatenato al campo `ButtonText` per definire il comando. Ad esempio, il **nuovo progetto** nel menu **file** diventa il comando file. NewProject.<br /><br /> Se il campo inglese `CanonicalName` non è specificato, l'IDE usa il campo `ButtonText` e rimuove tutti gli esclusi lettere, cifre, caratteri di sottolineatura e punti incorporati. Ad esempio, il testo del pulsante "& define Commands..." diventa DefineCommands, in cui la e commerciale, lo spazio e i puntini di sospensione vengono rimossi.<br /><br /> Se viene specificato il flag di `TextChanges` e il testo del comando viene modificato, il comando corrispondente riconosciuto dalla finestra di **comando** non viene modificato; rimane il formato canonico dei campi di `ButtonText` originale o di `CanonicalName` in inglese.|
|LocCanonicalName|Il campo `LocCanonicalName` si comporta in modo identico al campo `CanonicalName` inglese, ma consente di specificare il testo del comando localizzato. È possibile specificare entrambi i campi canonici. Poiché l'IDE analizza semplicemente il testo immesso nella finestra di **comando** e lo associa a un comando, sia il testo in inglese che quello non in lingua inglese possono essere associati allo stesso comando.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Button](../extensibility/button-element.md)|Definisce un elemento con cui l'utente può interagire.|
|[Elemento Menu](../extensibility/menu-element.md)|Definisce una singola voce di menu.|
|[Elemento Combo](../extensibility/combo-element.md)|Definisce i comandi che vengono visualizzati in una casella combinata.|

## <a name="see-also"></a>Vedere anche
- [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)