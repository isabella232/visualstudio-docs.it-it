---
title: Opzioni, Editor di testo, XML, Varie
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fed24e39b29907784d6101f7871f7a292850c457
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389354"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opzioni, Editor di testo, XML, Varie

Usare la pagina delle proprietà **Varie** per modificare le impostazioni di completamento automatico e dello schema per l'editor XML. Per aprire la finestra di dialogo **Opzioni**, fare clic sul menu **Strumenti** e quindi su **Opzioni**. Per accedere alla pagina delle proprietà **Varie**, espandere l'**Editor di testo** > **XML** > nodo **Varie**.

## <a name="auto-insert"></a>Inserimento automatico

**Tag di chiusura**

L'editor di testo aggiunge tag di chiusura durante la creazione di elementi XML. Se si seleziona il tag di inizio di un elemento, l'editor inserisce il tag di chiusura corrispondente, incluso un prefisso di spazio dei nomi corrispondente. Per impostazione predefinita, questa casella di controllo è selezionata.

**Virgolette per gli attributi**

Quando si creano attributi XML, l'editor inserisce i caratteri `="` e `"` e posiziona l'accento circonflesso (**^**) all'interno delle virgolette. Per impostazione predefinita, questa casella di controllo è selezionata.

**Dichiarazioni dello spazio dei nomi**

L'editor inserisce automaticamente le dichiarazioni dello spazio dei nomi ovunque siano necessarie. Per impostazione predefinita, questa casella di controllo è selezionata.

**Altri markup (commenti, CDATA)**

Commenti, CDATA, DOCTYPE, istruzioni di elaborazione e altri markup vengono completati automaticamente. Per impostazione predefinita, questa casella di controllo è selezionata.

## <a name="network"></a>Rete

**Scarica automaticamente le DTD e gli schemi**

Gli schemi e le DTD (Document Type Definitions) vengono scaricati automaticamente dalle posizioni HTTP. Questa funzionalità usa System.Net con il rilevamento automatico dei server proxy abilitato. Per impostazione predefinita, questa casella di controllo è selezionata.

## <a name="outlining"></a>struttura

**Attiva modalità struttura all'apertura del file**

Attiva la funzionalità struttura quando un file è aperto. Per impostazione predefinita, questa casella di controllo è selezionata.

## <a name="caching"></a>Memorizzazione nella cache

**Schemi**

Specifica il percorso della cache degli schemi. Il pulsante Sfoglia (...) consente di aprire la posizione corrente della cache dello schema in una nuova finestra. La posizione predefinita è  *\<directory di installazione di Management Studio>* \Xml\Schemas.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare documentazione XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Generazione di codice](../code-generation-in-visual-studio.md)