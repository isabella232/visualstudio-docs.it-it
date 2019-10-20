---
title: Varie, XML, editor di testo, finestra di dialogo Opzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d30564c11951d6ffec420c6a2ea95c41695de3dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656245"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Varie, XML, editor di testo, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa finestra di dialogo consente di modificare le impostazioni di completamento automatico e dello schema per l'editor XML. È possibile accedere alla finestra di dialogo **Opzioni** dal menu **strumenti** .

> [!NOTE]
> Queste impostazioni sono disponibili quando si seleziona la cartella **editor di testo** , la cartella **XML** e quindi l'opzione **varie** dalla finestra di dialogo **Opzioni** .

## <a name="auto-insert"></a>Inserimento automatico
 **Chiudi Tag** Se l'impostazione di completamento automatico è selezionata, l'editor aggiunge automaticamente un tag di fine quando si digita una parentesi uncinata chiusa (>) per chiudere un tag di inizio, se il tag non è già chiuso. Comportamento predefinito.

 Il completamento di un elemento vuoto non dipende dall'impostazione di completamento automatico. È sempre possibile completare automaticamente un elemento vuoto digitando una barra rovesciata (/).

 **Virgolette attributo** Quando si creano attributi XML, l'editor inserisce i caratteri `=" "` e posiziona il cursore (^) all'interno delle virgolette doppie.

 Selezionato per impostazione predefinita.

 **Dichiarazioni dello spazio dei nomi** L'editor inserisce automaticamente le dichiarazioni dello spazio dei nomi ogni volta che sono necessarie.

 Selezionato per impostazione predefinita.

 **Altro markup (commenti, CDATA)** Commenti, CDATA, DOCTYPE, istruzioni di elaborazione e altri markup vengono completati automaticamente.

 Selezionato per impostazione predefinita.

## <a name="network"></a>Rete
 **Scarica automaticamente le DTD e gli schemi** Gli schemi e le definizioni DTD (Document Type Definitions) vengono scaricati automaticamente da percorsi HTTP. Questa funzionalità usa System.Net con il rilevamento automatico dei server proxy abilitato.

 Selezionato per impostazione predefinita.

## <a name="outlining"></a>struttura
 Attiva **modalità struttura all'apertura dei file** Attiva la funzionalità di struttura quando viene aperto un file.

 Selezionato per impostazione predefinita.

## <a name="caching"></a>Memorizzazione nella cache
 **Schemi** di Specifica il percorso della cache dello schema. Il pulsante Sfoglia ( **...** ) consente di aprire la finestra di dialogo **Sfoglia directory** nella posizione corrente della cache dello schema. È possibile selezionare una directory diversa oppure selezionare una cartella nella finestra di dialogo, fare clic con il pulsante destro del mouse su di essa e scegliere **Apri** per vedere cosa si trova nella directory.

## <a name="see-also"></a>Vedere anche
 [Proprietà del documento XML,](../xml-tools/xml-document-properties-properties-window.md) [componenti dell'editor XML](../xml-tools/xml-editor-components.md) della finestra Proprietà
