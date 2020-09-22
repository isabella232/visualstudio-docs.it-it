---
title: Includere un file di dati in un'app ClickOnce
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cdc2154876724feb5c6a0329a2acc5df7ac80fbc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809146"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Procedura: Includere un file di dati in un'applicazione ClickOnce
A ogni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione installata viene assegnata una directory dei dati nel disco locale del computer di destinazione in cui l'applicazione è in grado di gestire i propri dati. I file di dati possono includere file di qualsiasi tipo: file di testo, file XML o persino file di database di Microsoft Access (*MDB*). Nelle procedure riportate di seguito viene illustrato come aggiungere un file di dati di qualsiasi tipo nell' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione.

### <a name="to-include-a-data-file-by-using-mageexe"></a>Per includere un file di dati tramite Mage.exe

1. Aggiungere il file di dati alla directory dell'applicazione con il resto dei file dell'applicazione.

    In genere, la directory dell'applicazione sarà una directory con l'etichetta della versione corrente della distribuzione, ad esempio v 1.0.0.0.

2. Aggiornare il manifesto dell'applicazione per elencare il file di dati.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    L'esecuzione di questa attività ricrea l'elenco dei file nel manifesto dell'applicazione e genera automaticamente le firme hash.

3. Aprire il manifesto dell'applicazione nel testo o nell'editor XML preferito e trovare l' `file` elemento per il file aggiunto di recente.

    Se è stato aggiunto un file XML denominato `Data.xml` , il file sarà simile all'esempio di codice seguente.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. Aggiungere l'attributo `type` a questo elemento e specificare un valore `data` .

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Firmare nuovamente il manifesto dell'applicazione usando la coppia di chiavi o il certificato, quindi firmare nuovamente il manifesto della distribuzione.

    È necessario firmare di nuovo il manifesto di distribuzione perché l'hash del manifesto dell'applicazione è stato modificato.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Per includere un file di dati tramite MageUI.exe

1. Aggiungere il file di dati alla directory dell'applicazione con il resto dei file dell'applicazione.

2. In genere, la directory dell'applicazione sarà una directory con l'etichetta della versione corrente della distribuzione, ad esempio v 1.0.0.0.

3. Nel menu **file** fare clic su **Apri** per aprire il manifesto dell'applicazione.

4. Selezionare la scheda **file** .

5. Nella casella di testo nella parte superiore della scheda immettere la directory che contiene i file dell'applicazione, quindi fare clic su **popola**.

     Il file di dati verrà visualizzato nella griglia.

6. Impostare il valore del **tipo di file** del file di dati su **dati**.

7. Salvare il manifesto dell'applicazione e quindi firmare nuovamente il file.

     *MageUI.exe* chiederà di firmare nuovamente il file.

8. Firma di nuovo il manifesto della distribuzione

     È necessario firmare di nuovo il manifesto di distribuzione perché l'hash del manifesto dell'applicazione è stato modificato.

## <a name="see-also"></a>Vedere anche
- [Accedere a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)