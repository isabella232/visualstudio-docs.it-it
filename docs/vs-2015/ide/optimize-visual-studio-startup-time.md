---
title: Ottimizzare il tempo di avvio | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f00bbc7741768852b5928b249dc7035bc440992
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670393"
---
# <a name="optimize-visual-studio-startup-time"></a>Ottimizzare il tempo di avvio di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Idealmente, Visual Studio deve sempre essere avviato nel più breve tempo possibile. Tuttavia, estensioni di Visual Studio e finestre degli strumenti aperte possono influire negativamente sul tempo di avvio poiché vengono caricate automaticamente all'avvio. La finestra **Gestisci prestazioni di Visual Studio** consente non solo di visualizzare le estensioni e le funzionalità che influiscono sul tempo di avvio di Visual Studio, ma anche di determinarne il comportamento di caricamento in modo da avere un maggior controllo sulla velocità di avvio di Visual Studio.

## <a name="control-startup-behavior"></a>Controllare il comportamento di avvio

Per evitare di estendere il tempo di avvio, Visual Studio 2017 e versioni successive evitano il caricamento delle estensioni all'avvio, usando un approccio di caricamento su richiesta. Ciò significa che le estensioni non si aprono subito dopo l'avvio di Visual Studio, aprendosi invece in modo asincrono in base alle esigenze dopo l'avvio. Inoltre, poiché le finestre degli strumenti lasciate aperte in una sessione precedente di Visual Studio possono rallentare l'avvio, esse vengono aperte in un modo più intelligente per evitare di compromettere il tempo di avvio.

Se Visual Studio rileva un avvio lento, viene visualizzato un messaggio popup che comunica quale estensione o finestra degli strumenti provoca il rallentamento. Il messaggio include anche un collegamento alla finestra di dialogo **Gestisci prestazioni di Visual Studio** che elenca le estensioni e le finestre degli strumenti che compromettono le prestazioni di avvio. Questa finestra di dialogo consente di modificare le impostazioni delle estensioni e delle finestre degli strumenti per migliorare le prestazioni di avvio.

![Gestisci prestazioni di Visual Studio-popup](../ide/media/vside-perfdialog-popup.PNG "Gestisci prestazioni di Visual Studio-popup")

La finestra di dialogo **Gestisci prestazioni di Visual Studio** include due categorie: **Estensioni** e **Finestre degli strumenti**.

### <a name="control-extensions"></a>Controllare le estensioni
Se un'estensione sta rallentando l'avvio di Visual Studio, essa viene visualizzata nella finestra di dialogo **Gestisci prestazioni di Visual Studio** quando si sceglie uno dei tipi di estensione. Se l'impatto sul tempo di avvio (indicato nella sezione **Impatto**) è eccessivamente elevato, è possibile scegliere di disabilitare sempre l'estensione all'avvio scegliendo il pulsante **Disabilita**. È possibile riabilitare l'estensione per le sessioni future mediante il Gestore estensioni o la finestra di dialogo Gestisci prestazioni di Visual Studio.

![Gestisci prestazioni di Visual Studio-estensioni](../ide/media/vside-perfdialog-extensions.PNG "Gestisci prestazioni di Visual Studio-estensioni")

Oltre alle estensioni di avvio, è anche possibile disabilitare le estensioni caricate mentre vengono caricate le soluzioni o mentre un utente digita. Scegliere lo scenario per visualizzare un elenco delle estensioni associate.

### <a name="control-tool-windows"></a>Controllare le finestre degli strumenti
Se una finestra degli strumenti sta rallentando l'avvio di Visual Studio, è possibile scegliere di lasciare il comportamento predefinito (senza alcun vantaggio per la velocità di avvio) oppure ignorarlo scegliendo uno dei due comportamenti seguenti:

- **Non visualizzare la finestra all'avvio:** se si sceglie questa opzione, la finestra degli strumenti specificata verrà sempre chiusa all'apertura di Visual Studio, anche se era stata lasciata aperta in una sessione precedente. È possibile aprire la finestra degli strumenti dal menu.
- **Nascondi automaticamente la finestra all'avvio:** se una finestra degli strumenti è stata lasciata aperta in una sessione precedente, scegliendo questa opzione il gruppo della finestra degli strumenti viene compresso all'avvio per evitarne l'inizializzazione. Questa è una scelta ottimale se si usa spesso una finestra degli strumenti, poiché la finestra degli strumenti rimane disponibile senza compromettere il tempo di avvio di Visual Studio.

![Gestire le prestazioni di Visual Studio-finestre degli strumenti](../ide/media/vside-perfdialog-toolwindows.PNG "Gestire le prestazioni di Visual Studio-finestre degli strumenti")

Se successivamente si cambia idea, è possibile ripristinare una qualsiasi di queste opzioni nella finestra di dialogo **Gestisci prestazioni di Visual Studio**. Per aprire la finestra di dialogo **Gestisci prestazioni di Visual Studio**, nella barra dei menu scegliere **Guida**, **Gestisci prestazioni di Visual Studio**.
