---
title: Opzioni, Editor di testo, JavaScript, IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b3b17416902bac2bcc7ff03adc39e548e63fb229
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879362"
---
# <a name="options-text-editor-javascript-intellisense"></a>Opzioni, Editor di testo, JavaScript, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [opzioni, Editor di testo, JavaScript, IntelliSense](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-javascript-intellisense).  
  
  
Utilizzare la pagina **IntelliSense** della finestra di dialogo **Opzioni** per modificare le impostazioni relative al funzionamento di IntelliSense per JavaScript. Per accedere alla pagina **IntelliSense** , scegliere **Strumenti**, **Opzioni** nella barra dei menu e quindi espandere **Editor di testo**, **JavaScript**, **IntelliSense.**  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
 La pagina **IntelliSense** include le sezioni seguenti:  
  
## <a name="validation"></a>Convalida  
 È possibile utilizzare queste opzioni per impostare le preferenze di convalida della sintassi da parte dell'editor JavaScript nel documento.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Mostra errori di sintassi**  
 Se questa casella di controllo non è selezionata, il codice JavaScript non mostra errori di sintassi. Risulta utile se si utilizza codice non scritto dall'utente e non si intende correggere alcun errore di sintassi.  
  
 Se questa casella di controllo è selezionata, è possibile selezionare la casella di controllo **Mostra errori come avvisi** .  
  
 **Mostra errori come avvisi**  
 Se questa casella di controllo è selezionata, gli errori JavaScript vengono mostrati come avvisi, anziché come errori nel relativo elenco.  
  
 **Download di riferimenti remoti (ad esempio, http://) per i file nel progetto di file esterni**  
 Se questa casella di controllo è selezionata e se all'esterno del contesto di un progetto è aperto un file JavaScript, in Visual Studio verranno scaricati i file JavaScript remoti a cui si fa riferimento nel file allo scopo di fornire informazioni relative a IntelliSense. Se questa opzione è selezionata, i file verranno scaricati nel momento in cui verranno inclusi come riferimento nel file JavaScript.  
  
> [!NOTE]
>  Per i progetti Web, i file remoti a cui viene fatto riferimento nel progetto vengono scaricati per impostazione predefinita.  
  
## <a name="statement-completion"></a>Completamento istruzioni  
 È possibile utilizzare queste opzioni per modificare il comportamento di completamento delle istruzioni IntelliSense.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Usa solo TAB o INVIO per il commit**  
 Se questa casella di controllo è selezionata, l'editor di codice JavaScript aggiungerà istruzioni agli elementi selezionati nell'elenco di completamento solo dopo aver premuto il tasto TAB o INVIO. Se questa casella di controllo non è selezionata, anche altri caratteri, tra cui punti, virgole, due punti, parentesi aperte e parentesi graffe aperte ({), possono aggiungere istruzioni agli elementi selezionati.  
  
## <a name="references"></a>Riferimenti  
 È possibile utilizzare queste opzioni per specificare i tipi di file .js IntelliSense che rientrano nell'ambito per tipi di progetti JavaScript diversi. I riferimenti di IntelliSense vengono in genere utilizzati per fornire il supporto IntelliSense per oggetti globali. È inoltre possibile utilizzare questa pagina per impostare l'ordine di caricamento per gli script che devono essere caricati al runtime e per aggiungere file di estensione IntelliSense.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Gruppi di riferimenti**  
 Questa opzione specifica il tipo di gruppo di riferimenti. Sono supportati tre gruppi di riferimenti:  
  
 È possibile utilizzare gruppi di riferimenti predefiniti per specificare che determinati file .js IntelliSense rientrino nell'ambito per progetti JavaScript diversi. Sono disponibili quattro gruppi di riferimenti:  
  
-   Implicito ( *versione*Windows), per le app [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] che usano JavaScript. I file inclusi in questo gruppo rientrano nell'ambito per ogni file con estensione js aperto nell'editor di codice per le app [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] che usano JavaScript.  
  
-   Implicito (Web), per progetti HTML5. I file inclusi in questo gruppo rientrano nell'ambito per ogni file .js aperto nell'editor di codice per questi tipi di progetto.  
  
-   Gruppi di riferimenti a processi di lavoro dedicati, per lavori Web HTML5. I file specificati in questo gruppo rientrano nell'ambito per i file .js con un riferimento esplicito a un gruppo di riferimenti a processi di lavoro dedicati.  
  
-   Generico, per altri tipi di progetti JavaScript.  
  
 **File inclusi**  
 Questa opzione specifica l'ordine di caricamento dei file nel contesto del servizio di linguaggio. È possibile configurare l'ordine utilizzando i pulsanti **Rimuovi**, **Sposta su**e **Sposta giù** . Per garantire il funzionamento di IntelliSense, un file dipendente da un altro dovrà essere caricato dopo quest'ultimo.  
  
> [!CAUTION]
>  Se un oggetto viene definito in modo non condizionale in due o più riferimenti impliciti, per definire l'oggetto verrà utilizzato l'ultimo riferimento in questo elenco.  
  
 **Aggiungi riferimento a gruppo corrente**  
 Questa opzione consente di aggiungere ulteriori file .js IntelliSense passando a quelli appropriati.  
  
## <a name="see-also"></a>Vedere anche  
 [IntelliSense per JavaScript](../../ide/javascript-intellisense.md)



