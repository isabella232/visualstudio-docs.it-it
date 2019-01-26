---
title: Elemento di stringhe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b62df361a965028240316c14da4c8c9ee8e578c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997702"
---
# <a name="strings-element"></a>Elemento Strings
L'elemento di stringhe deve contenere almeno un **ButtonText** elemento figlio. Tutti gli elementi figlio sono facoltativi. I caratteri XML non validi, come '&' e ' <' devono essere codificati come entità ('&amp;'e'&lt;' e così via).  
  
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
|language|Facoltativo. Language=".".|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|ButtonText|Questo campo e i cinque campi di testo seguente in una definizione di comando consentono di specificare il testo visualizzato nei vari menu. Per impostazione predefinita, il `ButtonText` campo viene visualizzato nel controller di menu. Il `ButtonText` campo diventa l'impostazione predefinita anche se gli altri campi di testo sono vuoti. Il `ButtonText` campo non può essere vuoto anche se vengono specificati gli altri campi di testo.|  
|ToolTipText|Il `ToolTipText` campo specifica il testo visualizzato nella descrizione comando per una voce di menu.<br /><br /> Se il `ToolTipText` campo è vuoto, il `ButtonText` campo viene usato.|  
|MenuText|Il `MenuText` campo specifica il testo visualizzato per un comando se si tratta del menu principale, una barra degli strumenti, in un menu di scelta rapida o in un sottomenu. Se il `MenuText` campo è vuoto, utilizza l'ambiente di sviluppo integrato (IDE) di `ButtonText` campo. Il `MenuText` campo può essere usato anche per la localizzazione.<br /><br /> Per i menu di scelta rapida di `MenuText` campo è il nome che viene visualizzato sulla barra degli strumenti, menu di scelta rapida che consente la personalizzazione del menu di scelta rapida nell'IDE. Pertanto, essere specifico in ciò che è denominare il menu di scelta rapida; ad esempio, usare "Menu di scelta rapida pacchetto Widget" anziché "Shortcut".<br /><br /> Se il `MenuText` campo non viene specificato, il `ButtonText` campo viene usato.|  
|CommandName|Il `CommandName` campo specifica il testo visualizzato nella categoria della tastiera la **comandi** scheda la **Personalizza** nella finestra di dialogo (disponibili facendo clic **Personalizza**su di **strumenti** menu).|  
|CanonicalName|La lingua inglese `CanonicalName` campo specifica il nome del comando nel testo inglese che può essere immesse nel **comando** finestra per eseguire la voce di menu. L'IDE rimuove qualsiasi caratteri che non sono lettere, cifre, caratteri di sottolineatura o punti incorporati. Questo testo viene quindi concatenato per il `ButtonText` campo per definire il comando. Ad esempio, **nuovo progetto** nel **File** menu diventa il comando, il file. NewProject.<br /><br /> Se la lingua inglese `CanonicalName` campo non viene specificato, l'IDE Usa il `ButtonText` campo e consente di eliminare i tutte tranne lettere, cifre, caratteri di sottolineatura e punti incorporati. Ad esempio, il testo del pulsante "e definire i comandi..." diventa DefineCommands, in cui vengono rimosse la e commerciale, lo spazio e sui puntini di sospensione.<br /><br /> Se il `TextChanges` flag è specificato e il testo del comando viene modificato, il comando corrispondente riconosciuto dal **comandi** finestra resta invariata e la forma canonica dell'originale rimane `ButtonText` o inglese `CanonicalName` campi.|  
|LocCanonicalName|Il `LocCanonicalName` campo si comporta esattamente come l'inglese `CanonicalName` campo Abilita ma testo del comando localizzata specificare. È possibile specificare entrambi i campi canonici. Poiché l'IDE appena analizza il testo immesso nella **comando** finestra e la associa con un comando, in inglese e testo non in lingua inglese può essere associato lo stesso comando.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Button](../extensibility/button-element.md)|Definisce un elemento che l'utente può interagire con.|  
|[Elemento Menu](../extensibility/menu-element.md)|Definisce una singola voce di menu.|  
|[Elemento Combo](../extensibility/combo-element.md)|Definisce i comandi che vengono visualizzati in una casella combinata.|  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)