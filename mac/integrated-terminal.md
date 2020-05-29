---
title: Visual Studio per Mac-terminale integrato
description: Visual Studio per Mac offre un ambiente di sviluppo integrato per creare applicazioni .NET in macOS, inclusi siti Web ASP.NET Core e progetti Xamarin per iOS, Android, Mac e Xamarin.Forms.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: d362938e8f0075591ea5d4ed8461d11395680b5c
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84185203"
---
# <a name="integrated-terminal"></a>Terminale integrato
In Visual Studio per Mac è possibile aprire una finestra del terminale integrata, iniziando inizialmente dalla radice della soluzione. Il terminale può essere utile per diversi tipi di situazioni: esecuzione di attività front-end (ad esempio, NPM, ng o VME), gestione dei contenitori, esecuzione di comandi Git avanzati, esecuzione di comandi Entity Framework, visualizzazione dell'output dell'interfaccia della riga di comando dotnet, aggiunta di pacchetti NuGet e altro ancora. 

Per aprire il terminale:
- Usare il tasto di scelta rapida **CTRL + "** per visualizzare o nascondere la finestra del terminale.
- Usare il menu del terminale **Visualizza** i \> **rilievi** \> **Terminal** .
- Usare il comando **Terminal** dalla barra di ricerca.

![* Il Visual Studio per Mac terminale integrato immediatamente dopo l'avvio. *](media/integrated-terminal-intro.png)

Per impostazione predefinita, quando viene avviato il terminale, viene eseguito quanto segue:
- Impostare la directory di lavoro sul percorso della soluzione corrente.
- Caricare la shell di sistema predefinita.

## <a name="search"></a>Cerca
È possibile cercare il contenuto della finestra del terminale utilizzando il menu **cerca > trova** .

![* Esperienza di ricerca nel terminale integrato Visual Studio per Mac *](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Tasti di scelta rapida del terminale
|Comandi|Scelte rapide da tastiera|
|-|-|
|Mostra/Nascondi la finestra del terminale|**CTRL +'**|
|Crea nuova istanza Terminal|**CTRL +'**|
|Scorri pagina verso l'alto|**PGSU**|
|Scorri pagina verso il basso|**PGGIÙ**|
|Scorrere i comandi usati in precedenza|**↑**, **↓**|
|Aumenta dimensioni carattere|**⌘ +**|
|Riduci dimensioni carattere|**⌘**|

## <a name="multiple-instances"></a>Istanze multiple
È possibile che più istanze del terminale vengano eseguite in qualsiasi momento. È possibile creare una nuova istanza usando il tasto di scelta rapida **CTRL +'** . Per spostarsi tra le istanze, fare clic sulla scheda relativa a ogni istanza oppure utilizzare il tasto di scelta rapida **CTRL + TAB** per utilizzare la finestra di dialogo selezione finestra.

![* Più istanze di Terminal in Visual Studio per Mac *](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Personalizzazione della finestra del terminale
### <a name="configuring-the-terminal-font"></a>Configurazione del tipo di carattere del terminale
È possibile modificare il tipo di carattere e le dimensioni usati per il contenuto del terminale nel riquadro preferenze > ambiente > tipi di carattere. Per impostazione predefinita, il tipo di carattere sarà identico al contenuto del riquadro di output, usando Menlo Regular, Size 11. È possibile impostarlo su qualsiasi tipo di carattere, indipendentemente dal tipo di carattere dell'editor.

![* Personalizzazione delle impostazioni del tipo di carattere per il terminale integrato *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Riutilizzo delle personalizzazioni del terminale di sistema
Il terminale integrato usa le stesse impostazioni predefinite e la stessa configurazione del terminale di sistema macOS. Ciò significa che le personalizzazioni del terminale (zsh, Oh-my-zsh e così via) funzionano anche nel terminale integrato.
