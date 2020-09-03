---
title: Opzioni, Editor di testo, XML, Varie
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dd468945b1ab9ac83b219b9c8c396f017065e2be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568126"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opzioni, Editor di testo, XML, Varie

Usare la pagina delle opzioni **Varie** per modificare le impostazioni di completamento automatico e dello schema per l'editor XML. Per accedere alle opzioni XML varie, scegliere **strumenti**  >  **Opzioni**  >  **editor di testo**  >  **XML**, quindi scegliere **varie**.

## <a name="auto-insert"></a>Inserimento automatico

**Chiudi i tag**

L'editor di testo aggiunge tag di chiusura durante la creazione di elementi XML. Se viene selezionato il tag di inizio di un elemento, viene inserito automaticamente il tag di chiusura corrispondente, che include un prefisso di spazio dei nomi corrispondente. Questa casella di controllo è selezionata per impostazione predefinita.

**Virgolette per gli attributi**

Quando si creano attributi XML, l'editor inserisce i `="` `"` caratteri e e posiziona il cursore ( **^** ) all'interno delle virgolette. Questa casella di controllo è selezionata per impostazione predefinita.

**Dichiarazioni degli spazi dei nomi**

Vengono inserite automaticamente le dichiarazioni degli spazi dei nomi, se necessarie. Questa casella di controllo è selezionata per impostazione predefinita.

**Altri markup (commenti, CDATA)**

Commenti, CDATA, DOCTYPE, istruzioni di elaborazione e altri markup vengono completati automaticamente. Questa casella di controllo è selezionata per impostazione predefinita.

## <a name="network"></a>Rete

**Scarica automaticamente le DTD e gli schemi**

Gli schemi e le definizioni DTD (Document Type Definitions) vengono scaricati automaticamente da percorsi HTTP. Questa caratteristica utilizza System.Net con il rilevamento automatico del server proxy. Questa casella di controllo è selezionata per impostazione predefinita.

## <a name="outlining"></a>struttura

**Attiva modalità struttura all'apertura dei file**

Attiva la modalità struttura quando viene aperto un file. Questa casella di controllo è selezionata per impostazione predefinita.

## <a name="caching"></a>Memorizzazione nella cache

**Schemi**

Specifica il percorso della cache degli schemi. Il pulsante **Sfoglia** consente di aprire la posizione corrente della cache dello schema in una nuova finestra. Il percorso predefinito è *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Vedere anche

- [Opzioni XML - Formattazione](options-text-editor-xml-formatting.md)
- [Strumenti XML in Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
