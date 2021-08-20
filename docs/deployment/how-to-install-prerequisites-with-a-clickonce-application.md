---
title: Installare i prerequisiti con un'app ClickOnce app
description: Informazioni su come selezionare i componenti dei prerequisiti da creare in un pacchetto insieme ClickOnce'applicazione quando viene installata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 9f319505fa0d17722e79274c993c1ccd54a8f5ce
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073851"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Procedura: Installare i prerequisiti con un'applicazione ClickOnce
Tutte le applicazioni richiedono che la versione corretta del .NET Framework sia installata in un computer prima di poter essere eseguite. Molte applicazioni hanno [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] anche altri prerequisiti. Quando si pubblica un'applicazione, è possibile scegliere un set di componenti prerequisiti da creare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] insieme all'applicazione. In fase di installazione verrà eseguito un controllo per ogni prerequisito per determinare se esiste già. in caso non verrà installato prima di installare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione.

 Anziché creare pacchetti e pubblicare prerequisiti, è anche possibile specificare un percorso di download per i componenti. Ad esempio, anziché includere i prerequisiti con ogni applicazione pubblicata, è possibile usare una condivisione file centralizzata o un percorso Web contenente i programmi di installazione per tutti i prerequisiti. In fase di installazione, i componenti verranno scaricati e installati da tale percorso.

> [!IMPORTANT]
> È consigliabile aggiungere i pacchetti del programma di installazione prerequisiti al computer di sviluppo prima di pubblicare la prima [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione. Per altre informazioni, [vedere Procedura: Includere prerequisiti con un'ClickOnce applicazione](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).

 I prerequisiti vengono gestiti nella **finestra di** dialogo Prerequisiti , accessibile dal riquadro **Pubblica** di Progettazione **Project .**

> [!NOTE]
> Oltre all'elenco predeterminato di prerequisiti, è possibile aggiungere componenti personalizzati all'elenco. Per altre informazioni, vedere Creazione [di pacchetti del programma di avvio automatico.](../deployment/creating-bootstrapper-packages.md)

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Per specificare i prerequisiti da installare con un'ClickOnce applicazione

1. Con un progetto selezionato in **Esplora soluzioni**, nel menu **Project** fare clic su **Proprietà**.

2. Selezionare il **riquadro** Pubblica.

3. Fare clic **sul pulsante** Prerequisiti per aprire la finestra **di dialogo** Prerequisiti .

4. Nella finestra di dialogo **Prerequisiti** verificare che la casella di controllo **Crea programma di installazione per installare componenti dei prerequisiti** sia selezionata.

5. **Nell'elenco Prerequisiti** controllare i componenti che si desidera installare e quindi fare clic su **OK.**

     I componenti selezionati verranno in pacchetto e pubblicati insieme all'applicazione.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Per specificare un percorso di download diverso per i prerequisiti

1. Con un progetto selezionato in **Esplora soluzioni**, nel menu **Project** fare clic su **Proprietà**.

2. Selezionare il **riquadro** Pubblica.

3. Fare clic **sul pulsante** Prerequisiti per aprire la finestra **di dialogo** Prerequisiti .

4. Nella finestra di dialogo **Prerequisiti** verificare che la casella di controllo **Crea programma di installazione per installare componenti dei prerequisiti** sia selezionata.

5. Nella sezione **Specificare il percorso di installazione per i prerequisiti** selezionare Scarica prerequisiti dal percorso **seguente.**

6. Selezionare un percorso dall'elenco a discesa oppure immettere un URL, un percorso di file o un percorso FTP, quindi fare clic su **OK.**

    > [!NOTE]
    > È necessario assicurarsi che i programmi di installazione per i componenti specificati esistano nel percorso specificato.

## <a name="see-also"></a>Vedi anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'ClickOnce di pubblicazione usando la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)