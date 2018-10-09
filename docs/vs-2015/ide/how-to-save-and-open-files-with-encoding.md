---
title: 'Procedura: Salvare e aprire file con codifica | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e505bf9c278ac40c835f40dad1f8897070fce0fc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532732"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Procedura: salvare e aprire file con codifica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile salvare i file con una codifica dei caratteri specifica per supportare le lingue bidirezionali. È anche possibile specificare una codifica all'apertura di un file, in modo che Visual Studio visualizzi il file correttamente.  
  
### <a name="to-save-a-file-with-encoding"></a>Per salvare un file con codifica  
  
1.  Scegliere **Salva con nome** dal menu **File** e fare clic sul pulsante del menu a discesa accanto al pulsante **Salva**.  
  
     Viene visualizzata la finestra di dialogo **Opzioni di salvataggio avanzate**.  
  
2.  In **Codifica** selezionare la codifica da usare per il file.  
  
3.  Facoltativamente, in **Terminazioni riga** selezionare il formato per i caratteri di fine della riga.  
  
     Questa opzione è utile se si prevede di scambiare il file con utenti di un altro sistema operativo.  
  
     Se si vuole usare un file che viene codificato in un modo specifico, è possibile indicare a Visual Studio di usare tale codifica all'apertura del file. Il metodo usato dipende se il file fa parte del progetto.  
  
### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Per aprire un file codificato che fa parte di un progetto  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file e scegliere **Apri con**.  
  
2.  Nella finestra di dialogo **Apri con** scegliere l'editor con cui aprire il file.  
  
     Molti editor di Visual Studio, ad esempio l'editor di form, rilevano automaticamente la codifica e aprono il file in modo appropriato. Se si sceglie un editor che consente di scegliere una codifica, viene visualizzata la finestra di dialogo **Codifica**.  
  
3.  Nella finestra di dialogo **Codifica** selezionare il tipo di codifica per l'editor.  
  
### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Per aprire un file codificato che non fa parte di un progetto  
  
1.  Nel menu **File** selezionare **Apri**, scegliere **File** o **File dal Web** e quindi selezionare il file da aprire.  
  
2.  Fare clic sul pulsante di menu a discesa accanto al pulsante **Apri** e scegliere **Apri con**.  
  
3.  Seguire i passaggi 2 e 3 della procedura precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [Globalizzazione di Windows Form e codifica](http://msdn.microsoft.com/library/22e8965d-a712-42b3-8167-3ee346bd70f9)   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)
