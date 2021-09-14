---
title: Opzioni, Editor di testo, JavaScript, IntelliSense
description: Informazioni su come usare la pagina IntelliSense della finestra di dialogo Opzioni per modificare le impostazioni che influiscono sul comportamento di IntelliSense per JavaScript.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.IntelliSense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 051711a9d6dfe861f37e741ae9ecabfbf741012e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628668"
---
# <a name="options-dialog-box-text-editor--javascript--intellisense"></a>Finestra di dialogo Opzioni: \> IntelliSense JavaScript dell'editor \> di testo

Utilizzare la pagina **IntelliSense** della finestra di dialogo **Opzioni** per modificare le impostazioni relative al funzionamento di IntelliSense per JavaScript. Per accedere alla pagina **IntelliSense**, scegliere **Strumenti** > **Opzioni** sulla barra dei menu e quindi espandere **Editor di testo** > **JavaScript/TypeScript** > **IntelliSense**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

La pagina **IntelliSense** include le sezioni seguenti:

## <a name="statement-completion"></a>Completamento istruzioni

È possibile utilizzare queste opzioni per modificare il comportamento di completamento delle istruzioni IntelliSense.

### <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**Usare solo TAB o INVIO per eseguire il commit**

Se si seleziona questa casella di controllo, l'editor di codice JavaScript aggiungerà istruzioni agli elementi selezionati nell'elenco di completamento solo dopo che è stato premuto **TAB** o **INVIO**. Se si deseleziona questa casella di controllo, anche altri caratteri, tra cui punti, virgole, due punti, parentesi aperte e parentesi graffe aperte ({), possono aggiungere istruzioni agli elementi selezionati.

## <a name="references"></a>Riferimenti

È possibile utilizzare queste opzioni per specificare i tipi di file .js IntelliSense che rientrano nell'ambito per tipi di progetti JavaScript diversi. I riferimenti di IntelliSense vengono in genere utilizzati per fornire il supporto IntelliSense per oggetti globali. È inoltre possibile utilizzare questa pagina per impostare l'ordine di caricamento per gli script che devono essere caricati al runtime e per aggiungere file di estensione IntelliSense.

### <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**Gruppi di riferimento**

Questa opzione specifica il tipo di gruppo di riferimenti. Sono supportati tre gruppi di riferimenti:

È possibile utilizzare gruppi di riferimenti predefiniti per specificare che determinati file .js IntelliSense rientrino nell'ambito per progetti JavaScript diversi. Sono disponibili quattro gruppi di riferimenti:

- Implicito ( *versione* Windows), per le app [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] che usano JavaScript. I file inclusi in questo gruppo rientrano nell'ambito per ogni file con estensione js aperto nell'editor di codice per le app [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] che usano JavaScript.

- Implicito (Web), per progetti HTML5. I file inclusi in questo gruppo rientrano nell'ambito per ogni file .js aperto nell'editor di codice per questi tipi di progetto.

- Gruppi di riferimenti a ruoli di lavoro dedicati, per ruoli di lavoro HTML5. I file specificati in questo gruppo rientrano nell'ambito per i file .js con un riferimento esplicito a un gruppo di riferimenti a processi di lavoro dedicati.

- Generico, per altri tipi di progetti JavaScript.

**File inclusi**

Questa opzione specifica l'ordine di caricamento dei file nel contesto del servizio di linguaggio. È possibile configurare l'ordine utilizzando i pulsanti **Rimuovi**, **Sposta su** e **Sposta giù** . Per garantire il funzionamento di IntelliSense, un file dipendente da un altro dovrà essere caricato dopo quest'ultimo.

> [!CAUTION]
> Se un oggetto viene definito in modo non condizionale in due o più riferimenti impliciti, per definire l'oggetto verrà utilizzato l'ultimo riferimento in questo elenco.

**Aggiungi riferimento a gruppo corrente**

Questa opzione consente di aggiungere ulteriori file .js IntelliSense passando a quelli appropriati.

**Download di riferimenti remoti (ad esempio, http://) per i file nel progetto di file esterni**

Se questa casella di controllo è selezionata e se all'esterno del contesto del progetto è aperto un file JavaScript, Visual Studio scarica i file JavaScript remoti a cui si fa riferimento nel file allo scopo di rendere disponibili informazioni IntelliSense. Se questa opzione è selezionata, i file vengono scaricati nel momento in cui vengono inclusi come riferimento nel file JavaScript.

> [!NOTE]
> Per i progetti Web, i file remoti a cui viene fatto riferimento nel progetto vengono scaricati per impostazione predefinita.

## <a name="see-also"></a>Vedi anche

- [IntelliSense per JavaScript](../../ide/javascript-intellisense.md)