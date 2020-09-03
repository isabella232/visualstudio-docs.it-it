---
title: Opzioni, Editor di testo, JavaScript, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b0d9dec8ec9b3eb8860bb8b3a4ed8f7347aa54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662237"
---
# <a name="options-text-editor-javascript-intellisense"></a>Opzioni, Editor di testo, JavaScript, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilizzare la pagina **IntelliSense** della finestra di dialogo **Opzioni** per modificare le impostazioni relative al funzionamento di IntelliSense per JavaScript. Per accedere alla pagina **IntelliSense** , scegliere **Strumenti**, **Opzioni** nella barra dei menu e quindi espandere **Editor di testo**, **JavaScript**, **IntelliSense.**

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 La pagina **IntelliSense** include le sezioni seguenti:

## <a name="validation"></a>Convalida
 È possibile utilizzare queste opzioni per impostare le preferenze di convalida della sintassi da parte dell'editor JavaScript nel documento.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Mostra errori di sintassi** Se questa casella di controllo non è selezionata, l'editor di codice JavaScript non Mostra errori di sintassi. Risulta utile se si utilizza codice non scritto dall'utente e non si intende correggere alcun errore di sintassi.

 Se questa casella di controllo è selezionata, è possibile selezionare la casella di controllo **Mostra errori come avvisi** .

 **Mostra errori come avvisi** Se questa casella di controllo è selezionata, gli errori JavaScript vengono visualizzati come avvisi anziché come errori nell'elenco errori.

 **Scaricare i riferimenti remoti (ad esempio, http://) per i file nel progetto di file esterni** Se questa casella di controllo è selezionata e se si dispone di un file JavaScript aperto al di fuori del contesto di un progetto, Visual Studio scaricherà i file JavaScript remoti a cui si fa riferimento nel file allo scopo di fornire informazioni IntelliSense. Se questa opzione è selezionata, i file verranno scaricati nel momento in cui verranno inclusi come riferimento nel file JavaScript.

> [!NOTE]
> Per i progetti Web, i file remoti a cui viene fatto riferimento nel progetto vengono scaricati per impostazione predefinita.

## <a name="statement-completion"></a>Completamento istruzioni
 È possibile utilizzare queste opzioni per modificare il comportamento di completamento delle istruzioni IntelliSense.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Usa solo TAB o invio per il commit** Se questa casella di controllo è selezionata, l'editor di codice JavaScript aggiunge le istruzioni con gli elementi selezionati nell'elenco di completamento solo dopo aver scelto la scheda o il tasto INVIO. Se questa casella di controllo non è selezionata, anche altri caratteri, tra cui punti, virgole, due punti, parentesi aperte e parentesi graffe aperte ({), possono aggiungere istruzioni agli elementi selezionati.

## <a name="references"></a>Riferimenti
 È possibile utilizzare queste opzioni per specificare i tipi di file .js IntelliSense che rientrano nell'ambito per tipi di progetti JavaScript diversi. I riferimenti di IntelliSense vengono in genere utilizzati per fornire il supporto IntelliSense per oggetti globali. È inoltre possibile utilizzare questa pagina per impostare l'ordine di caricamento per gli script che devono essere caricati al runtime e per aggiungere file di estensione IntelliSense.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Gruppi di riferimento** Questa opzione specifica il tipo di gruppo di riferimenti. Sono supportati tre gruppi di riferimenti:

 È possibile utilizzare gruppi di riferimenti predefiniti per specificare che determinati file .js IntelliSense rientrino nell'ambito per progetti JavaScript diversi. Sono disponibili quattro gruppi di riferimenti:

- Implicito ( *versione*Windows), per le app [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] che usano JavaScript. I file inclusi in questo gruppo rientrano nell'ambito per ogni file con estensione js aperto nell'editor di codice per le app [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] che usano JavaScript.

- Implicito (Web), per progetti HTML5. I file inclusi in questo gruppo rientrano nell'ambito per ogni file .js aperto nell'editor di codice per questi tipi di progetto.

- Gruppi di riferimenti a processi di lavoro dedicati, per lavori Web HTML5. I file specificati in questo gruppo rientrano nell'ambito per i file .js con un riferimento esplicito a un gruppo di riferimenti a processi di lavoro dedicati.

- Generico, per altri tipi di progetti JavaScript.

  **File inclusi** Questa opzione specifica l'ordine di caricamento dei file nel contesto del servizio di linguaggio. È possibile configurare l'ordine utilizzando i pulsanti **Rimuovi**, **Sposta su**e **Sposta giù** . Per garantire il funzionamento di IntelliSense, un file dipendente da un altro dovrà essere caricato dopo quest'ultimo.

> [!CAUTION]
> Se un oggetto viene definito in modo non condizionale in due o più riferimenti impliciti, per definire l'oggetto verrà utilizzato l'ultimo riferimento in questo elenco.

 **Aggiungere un riferimento al gruppo** Questa opzione consente di aggiungere altri file IntelliSense. js esplorando i file appropriati.

## <a name="see-also"></a>Vedere anche
 [IntelliSense per JavaScript](../../ide/javascript-intellisense.md)
