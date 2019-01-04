---
title: Varie, XML, editor di testo, finestra di dialogo Opzioni
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85af563d9fb20b12785a410cf7df7e612d17dbee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941401"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Varie, XML, Editor di testo, finestra di dialogo Opzioni

Questa finestra di dialogo consente di modificare le impostazioni di completamento automatico e dello schema per l'editor XML. È possibile accedere la **le opzioni** dalla finestra di dialogo il **strumenti** menu.

> [!NOTE]
> Queste impostazioni sono disponibili quando si seleziona il **Editor di testo** cartella, la **XML** cartella e quindi il **varie** opzione il **opzioni** finestra di dialogo.


## <a name="auto-insert"></a>Inserimento automatico
 **Tag di chiusura**

 Se l'impostazione di completamento automatico è selezionata, l'editor aggiunge automaticamente un tag di fine quando si digita una parentesi uncinata chiusa (>) per chiudere un tag di inizio, se il tag non è stato ancora chiuso. Comportamento predefinito.

 Il completamento di un elemento vuoto non dipende dall'impostazione di completamento automatico. È sempre possibile completare automaticamente un elemento vuoto digitando una barra rovesciata (/).

 **Virgolette per gli attributi**

 Quando si creano attributi XML, l'editor inserisce i caratteri `=" "` e posiziona l'accento circonflesso (^) all'interno delle virgolette.

 Selezionato per impostazione predefinita.

 **Dichiarazioni dello spazio dei nomi**

 L'editor inserisce automaticamente le dichiarazioni dello spazio dei nomi ovunque siano necessarie.

 Selezionato per impostazione predefinita.

 **Altri markup (commenti, CDATA)**

 Commenti, CDATA, DOCTYPE, istruzioni di elaborazione e altri markup vengono completati automaticamente.

 Selezionato per impostazione predefinita.

## <a name="network"></a>Rete
 **Scarica automaticamente le DTD e gli schemi**

 Gli schemi e le DTD (Document Type Definitions) vengono scaricati automaticamente dalle posizioni HTTP. Questa funzionalità usa System.Net con il rilevamento automatico dei server proxy abilitato.

 Selezionato per impostazione predefinita.

## <a name="outlining"></a>struttura
 **Attiva modalità struttura all'apertura del file**

 Attiva la funzionalità struttura quando un file è aperto.

 Selezionato per impostazione predefinita.

## <a name="caching"></a>Memorizzazione nella cache
 **Schemi**

 Specifica il percorso della cache degli schemi. Il pulsante Sfoglia (**...** ) consente di aprire la **Sfoglia Directory** finestra di dialogo nella posizione corrente dello schema della cache. È possibile selezionare una directory diversa, oppure è possibile selezionare una cartella nella finestra di dialogo, pulsante destro del mouse, scegliere **aperto** per visualizzare gli elementi nella directory.

## <a name="see-also"></a>Vedere anche

- [Proprietà di documento XML, finestra proprietà](../xml-tools/xml-document-properties-properties-window.md)
- [Componenti dell'editor XML](../xml-tools/xml-editor-components.md)