---
title: Opzioni, Editor di testo, Estensione di file | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.file_extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26c53633bc55efcf95ffbc579e24d2d61e4a0932
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662265"
---
# <a name="options-text-editor-file-extension"></a>Opzioni, Editor di testo, Estensione file
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La finestra di dialogo Opzioni consente di specificare il modo in cui tutti i file con determinate estensioni verranno gestiti nell'ambiente di sviluppo integrato (IDE) di Visual Studio. Per ogni **estensione** è possibile selezionare uno strumento di modifica. In questo modo è possibile scegliere l'editor dell'IDE o la finestra di progettazione in cui verranno aperti i documenti di un determinato tipo. Per visualizzare queste opzioni, scegliere **Opzioni** dal **Strumenti**, espandere il nodo **Editor di testo** e selezionare **Estensione di file**.

 Quando si seleziona un'opzione "con codifica", ogni volta che si apre un documento del tipo specifico viene visualizzata una finestra di dialogo che consente di selezionare uno schema di codifica per il documento. Ciò può rivelarsi utile se si preparano versioni dei documenti di progetto da usare in piattaforme diverse o con lingue di destinazione diverse.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Estensione** di Digitare l'estensione di file di cui si desidera definire l'esperienza di modifica nell'IDE.

 **Editor** di Selezionare la finestra di progettazione o l'editor dell'IDE in cui si apriranno i documenti con questa estensione. Quando si seleziona un'opzione "con codifica", ogni volta che si apre un documento del tipo specifico viene visualizzata una finestra di dialogo che consente di selezionare uno schema di codifica.

 **Aggiungi** Aggiunge una voce che include l'**Estensione** e lo **Strumento di modifica** specificati all'elenco delle estensioni.

 **Rimuovi** Elimina la voce selezionata dall'elenco di estensioni.

 Elenco estensioni elenca tutte le estensioni per le quali è stata specificata un'esperienza di modifica.

 Esegui **mapping di file con estensione a** Selezionare questa opzione se si desidera specificare il modo in cui i file senza estensione verranno gestiti dall'IDE.

 **Opzioni del file con estensione** Fornisce lo stesso elenco di **Editor**. Selezionare la finestra di progettazione o l'editor dell'IDE in cui verranno aperti i documenti senza estensione di file.

## <a name="see-also"></a>Vedere anche
 [Procedura: Gestire le modalità dell'editor](../../ide/how-to-manage-editor-modes.md)
