---
title: Firmare i file di installazione con SignTool.exe (ClickOnce)
description: Informazioni su come usare SignTool.exe per firmare un programma di installazione per ClickOnce applicazioni, in modo da garantire che i file manomissioni non siano installati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 668c37da5410b0764c9ab84fce44506f8152c68e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160634"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Procedura: Firmare i file di installazione con SignTool.exe (ClickOnce)
È possibile usare *SignTool.exe* per firmare un programma di installazione (*setup.exe*). Questo processo aiuta ad assicurare che nei computer degli utenti finali non siano installati file alterati.

 Per impostazione predefinita, ClickOnce include manifesti firmati e un programma di installazione firmato. Se tuttavia si vogliono modificare i parametri del programma di installazione in un secondo momento, sarà necessario firmare il programma in un secondo momento. Se si cambiano i parametri dopo la firma del programma di installazione, la firma sarà danneggiata.

 La procedura seguente genera manifesti non firmati e un programma di installazione non firmato. La firma ClickOnce è quindi abilitata in seguito in Visual Studio per generare manifesti firmati. Il programma di installazione è lasciato non firmato, in modo che il cliente possa firmare il file eseguibile con il proprio certificato.

### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Per generare un programma di installazione non firmato e firmarlo in seguito

1. Installare nel computer di sviluppo il certificato da usare per la firma del manifesto.

2. Selezionare il progetto in **Esplora soluzioni**.

3. Nel menu **Project** scegliere *Proprietà NomeProgetto* .

4. Nella pagina **Firma** deselezionare l'opzione **Firma i manifesti ClickOnce**.

5. Nella pagina **Pubblica** fare clic su **Prerequisiti**.

6. Verificare che siano selezionati tutti i prerequisiti, quindi fare clic su **OK**.

7. Nella pagina **Pubblica** verificare le impostazioni di pubblicazione e quindi fare clic su **Pubblica**.

     La soluzione pubblica il manifesto dell'applicazione non firmato, il manifesto della distribuzione non firmato, i file specifici della versione e il programma di installazione non firmato nel percorso della cartella di pubblicazione.

8. Nella pagina **Pubblica** fare clic su **Prerequisiti**.

9. Nella finestra di dialogo **Prerequisiti** deselezionare l'opzione **Crea programma di installazione per installare componenti dei prerequisiti**.

10. Nella pagina **Pubblica** verificare le impostazioni di pubblicazione e quindi fare clic su **Pubblica**.

     La soluzione pubblica il manifesto dell'applicazione firmato, il manifesto della distribuzione firmato e i file specifici della versione nel percorso della cartella di pubblicazione. Il programma di installazione non firmato non sarà sovrascritto dal processo di pubblicazione.

11. Aprire un prompt dei comandi nel sito del cliente.

12. Passare alla directory che contiene il file con estensione *exe*.

13. Firmare il file con estensione *exe* con il comando seguente:

    ```cmd
    signtool sign /sha1 CertificateHash Setup.exe
    signtool sign /f CertFileName Setup.exe
    ```

     Per firmare il programma di installazione, ad esempio, usare uno dei comandi seguenti:

    ```cmd
    signtool sign /sha1 CCB... Setup.exe
    signtool sign /f CertFileName Setup.exe
    ```

## <a name="see-also"></a>Vedi anche
- [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
