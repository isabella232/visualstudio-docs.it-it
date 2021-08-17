---
title: Includere un file di dati in un'app ClickOnce dati
description: Informazioni su come aggiungere un file di dati di qualsiasi tipo nell'applicazione ClickOnce da archiviare in una directory di dati nel disco locale del computer di destinazione.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 225c24e4bb743b26a137b68e206a5937963f6e28
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080598"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Procedura: Includere un file di dati in un'applicazione ClickOnce
A ogni applicazione installata viene assegnata una directory dati sul disco locale del computer di destinazione in cui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione può gestire i propri dati. I file di dati possono includere file di qualsiasi tipo: file di testo, file XML o anche file di database di Microsoft Access *(con estensione mdb).* Le procedure seguenti illustrano come aggiungere un file di dati di qualsiasi tipo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nell'applicazione.

### <a name="to-include-a-data-file-by-using-mageexe"></a>Per includere un file di dati usando Mage.exe

1. Aggiungere il file di dati alla directory dell'applicazione con il resto dei file dell'applicazione.

    In genere, la directory dell'applicazione sarà una directory etichettata con la versione corrente della distribuzione, ad esempio v1.0.0.0.

2. Aggiornare il manifesto dell'applicazione per elencare il file di dati.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    L'esecuzione di questa attività crea nuovamente l'elenco di file nel manifesto dell'applicazione e genera automaticamente le firme hash.

3. Aprire il manifesto dell'applicazione nell'editor di testo o XML preferito e trovare `file` l'elemento per il file aggiunto di recente.

    Se è stato aggiunto un file XML denominato `Data.xml` , il file sarà simile all'esempio di codice seguente.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. Aggiungere `type` l'attributo a questo elemento e specificarlo con il valore `data` .

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Firmare nuovamente il manifesto dell'applicazione usando la coppia di chiavi o il certificato e quindi firmare di nuovo il manifesto della distribuzione.

    È necessario firmare nuovamente il manifesto della distribuzione perché l'hash del manifesto dell'applicazione è stato modificato.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Per includere un file di dati usando MageUI.exe

1. Aggiungere il file di dati alla directory dell'applicazione con il resto dei file dell'applicazione.

2. In genere, la directory dell'applicazione sarà una directory etichettata con la versione corrente della distribuzione, ad esempio v1.0.0.0.

3. Scegliere **Apri** dal menu File **per** aprire il manifesto dell'applicazione.

4. Selezionare la **scheda** File.

5. Nella casella di testo nella parte superiore della scheda immettere la directory che contiene i file dell'applicazione e quindi fare clic su **Popola**.

     Il file di dati verrà visualizzato nella griglia.

6. Impostare il **valore Tipo file** del file di dati su **Dati**.

7. Salvare il manifesto dell'applicazione e quindi firmare nuovamente il file.

     *MageUI.exe* verrà richiesto di firmare nuovamente il file.

8. Firmare di nuovo il manifesto della distribuzione

     È necessario firmare nuovamente il manifesto della distribuzione perché l'hash del manifesto dell'applicazione è stato modificato.

## <a name="see-also"></a>Vedi anche
- [Accedere a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)