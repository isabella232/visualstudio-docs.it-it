---
title: Elemento Strings | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0eae2fd7490269d713beb9950163071dd3ba32f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160564"
---
# <a name="strings-element"></a>Elemento Strings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'elemento Strings deve contenere almeno un elemento figlio **ButtonText** . Tutti gli altri elementi figlio sono facoltativi. I caratteri XML non validi, ad esempio ' &' è <', devono essere codificati come entità (' &amp; ' è &lt; ' e così via).  
  
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
|Linguaggio|facoltativo. Language = ".".|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|ButtonText|Questo campo e i cinque campi di testo seguenti in una definizione di comando consentono di specificare il testo visualizzato in vari menu. Per impostazione predefinita, il `ButtonText` campo viene visualizzato nei controller di menu. Il `ButtonText` campo diventa anche il valore predefinito se gli altri campi di testo sono vuoti. Il `ButtonText` campo non può essere vuoto anche se gli altri campi di testo sono specificati.|  
|ToolTipText|Il `ToolTipText` campo specifica il testo visualizzato nella descrizione comando per una voce di menu.<br /><br /> Se il `ToolTipText` campo è vuoto, `ButtonText` viene utilizzato il campo.|  
|MenuText|Il `MenuText` campo specifica il testo visualizzato per un comando se si trova nel menu principale, in una barra degli strumenti, in un menu di scelta rapida o in un sottomenu. Se il `MenuText` campo è vuoto, il Integrated Development Environment (IDE) usa il `ButtonText` campo. Il `MenuText` campo può essere usato anche per la localizzazione.<br /><br /> Per i menu di scelta rapida, il `MenuText` campo è il nome visualizzato nella barra degli strumenti dei menu di scelta rapida, che consente di personalizzare i menu di scelta rapida nell'IDE. Pertanto, è necessario specificare il nome del menu di scelta rapida. ad esempio, usare "menu di scelta rapida del pacchetto widget" invece di "collegamento".<br /><br /> Se il `MenuText` campo non è specificato, `ButtonText` viene utilizzato il campo.|  
|CommandName|Il `CommandName` campo specifica il testo visualizzato nella categoria tastiera nella scheda **comandi** della finestra di dialogo **Personalizza** , disponibile scegliendo **Personalizza** dal menu **strumenti** .|  
|CanonicalName|Il `CanonicalName` campo inglese specifica il nome del comando nel testo in lingua inglese che è possibile immettere nella finestra di **comando** per eseguire la voce di menu. L'IDE rimuove tutti i caratteri che non sono lettere, cifre, caratteri di sottolineatura o punti incorporati. Questo testo viene quindi concatenato al `ButtonText` campo per definire il comando. Ad esempio, il **nuovo progetto** nel menu **file** diventa il comando file. NewProject.<br /><br /> Se il `CanonicalName` campo inglese non è specificato, l'IDE usa il `ButtonText` campo e rimuove tutte le lettere, le cifre, i caratteri di sottolineatura e i punti incorporati. Ad esempio, il testo del pulsante "&define Commands..." diventa DefineCommands, in cui la e commerciale, lo spazio e i puntini di sospensione vengono rimossi.<br /><br /> Se il `TextChanges` flag viene specificato e il testo del comando viene modificato, il comando corrispondente riconosciuto dalla finestra di **comando** non cambia; rimane la forma canonica dei `ButtonText` campi originali o inglesi `CanonicalName` .|  
|LocCanonicalName|Il `LocCanonicalName` campo si comporta in modo identico al `CanonicalName` campo inglese, ma consente di specificare il testo del comando localizzato. È possibile specificare entrambi i campi canonici. Poiché l'IDE analizza semplicemente il testo immesso nella finestra di **comando** e lo associa a un comando, sia il testo in inglese che quello non in lingua inglese possono essere associati allo stesso comando.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Button](../extensibility/button-element.md)|Definisce un elemento con cui l'utente può interagire.|  
|[Elemento Menu](../extensibility/menu-element.md)|Definisce una singola voce di menu.|  
|[Elemento Combo](../extensibility/combo-element.md)|Definisce i comandi che vengono visualizzati in una casella combinata.|  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
