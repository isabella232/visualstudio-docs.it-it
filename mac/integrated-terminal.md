---
title: Visual Studio per Mac - Terminale integrato
description: Uso del terminale integrato in Visual Studio per Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: 0dd93498967139083ed8828ee6d6757db52584874b9c93855604d06b8c6eacd0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121407348"
---
# <a name="integrated-terminal"></a>Terminale integrato
In Visual Studio per Mac è possibile aprire una finestra del terminale integrato, inizialmente a partire dalla radice della soluzione. Il terminale può essere utile per diversi tipi di situazioni: esecuzione di attività front-end (ad esempio npm, ng o vue), gestione di contenitori, esecuzione di comandi Git avanzati, esecuzione di comandi Entity Framework, visualizzazione dell'output dell'interfaccia della riga di comando dotnet, aggiunta di pacchetti NuGet e altro ancora. 

Per aprire il terminale:
- Usare i **tasti di scelta rapida CTRL+'** per visualizzare o nascondere la finestra del terminale.
- Usare  il menu \> **Visualizza terminale.**
- Usare il **comando terminale** dalla barra di ricerca.

![*Il Visual Studio per Mac terminale integrato immediatamente dopo l'avvio.*](media/integrated-terminal-intro.png)

Per impostazione predefinita, all'avvio del terminale:
- Impostare la directory di lavoro sul percorso della soluzione corrente.
- Caricare la shell di sistema predefinita.

## <a name="search"></a>Cerca
È possibile cercare il contenuto della finestra del terminale usando il menu Cerca > **Trova.**

![*Esperienza di ricerca nel Visual Studio per Mac terminale integrato*](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Tasti di scelta rapida del terminale
|Comandi|Scelte rapide da tastiera|
|-|-|
|Mostra/Nascondi la finestra del terminale|**CTRL+ '**|
|Creare una nuova istanza del terminale|**CTRL+'**|
|Scorri pagina verso l'alto|**PGSU**|
|Scorri pagina verso il basso|**PGGIÙ**|
|Scorrere i comandi usati in precedenza|**↑**, **↓**|
|Aumentare le dimensioni del carattere|**⌘+**|
|Ridurre le dimensioni del carattere|**⌘-**|

## <a name="multiple-instances"></a>Istanze multiple
È possibile che più istanze del terminale siano in esecuzione in qualsiasi momento. È possibile creare una nuova istanza usando i tasti **di scelta rapida CTRL+'** . È possibile passare da un'istanza all'altra facendo clic sulla scheda per ogni istanza o usando il tasto di scelta **rapida CTRL+TAB** per usare la finestra di dialogo di selezione finestra.

![*Più istanze del terminale in Visual Studio per Mac*](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Personalizzazione della finestra del terminale
### <a name="configuring-the-terminal-font"></a>Configurazione del tipo di carattere del terminale
È possibile modificare il tipo di carattere e le dimensioni usati per Contenuto terminale nel riquadro Preferenze > ambiente > tipi di carattere. Per impostazione predefinita, il tipo di carattere sarà lo stesso Finestra di output, usando Menlo Regular, dimensione 11. È possibile impostarlo su qualsiasi tipo di carattere, indipendentemente dal tipo di carattere dell'editor.

![*Personalizzazione delle impostazioni dei caratteri per il terminale integrato*](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Riutilizzo delle personalizzazioni dei terminali di sistema
Il terminale integrato usa le stesse impostazioni predefinite e la stessa configurazione del terminale di sistema macOS. Ciò significa che le personalizzazioni del terminale (zsh, oh-my-zsh e così via) funzionano anche nel terminale integrato.
