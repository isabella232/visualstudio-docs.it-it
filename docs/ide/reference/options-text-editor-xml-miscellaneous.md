---
title: Opzioni, Editor di testo, XML, Varie
description: Informazioni su come usare la pagina Varie nella sezione XAML per modificare il completamento automatico e le impostazioni dello schema per l'editor XML.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: ed004ee7208ab599aab568d515af6b9de45d2e05a2fd35525e0a7bd082bf1112
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372172"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opzioni, Editor di testo, XML, Varie

Usare la pagina delle opzioni **Varie** per modificare le impostazioni di completamento automatico e dello schema per l'editor XML. Per accedere alle varie opzioni XML, scegliere Strumenti   >  **Opzioni**  >  **Editor**  >   di testo XML e quindi scegliere Varie .

## <a name="auto-insert"></a>Inserimento automatico

**Chiudi i tag**

L'editor di testo aggiunge tag di chiusura durante la creazione di elementi XML. Se viene selezionato il tag di inizio di un elemento, viene inserito automaticamente il tag di chiusura corrispondente, che include un prefisso di spazio dei nomi corrispondente. Questa casella di controllo è selezionata per impostazione predefinita.

**Virgolette per gli attributi**

Durante la creazione di attributi XML, l'editor inserisce i caratteri e e posiziona il `="` `"` cursore ( **^** ) tra virgolette. Questa casella di controllo è selezionata per impostazione predefinita.

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

## <a name="see-also"></a>Vedi anche

- [Opzioni XML - Formattazione](options-text-editor-xml-formatting.md)
- [Strumenti XML in Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
