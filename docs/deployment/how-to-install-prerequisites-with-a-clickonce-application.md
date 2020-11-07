---
title: Installare i prerequisiti con un'app ClickOnce
description: Informazioni su come selezionare i componenti dei prerequisiti da creare in un pacchetto insieme all'applicazione ClickOnce durante l'installazione.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4a2f2b951881208d3995aeb1f5f1f655b80674f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349932"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Procedura: Installare i prerequisiti con un'applicazione ClickOnce
Per tutte le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni è necessario che la versione corretta del .NET Framework sia installata in un computer prima di poter essere eseguita. molte applicazioni hanno anche altri prerequisiti. Quando si pubblica un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, è possibile scegliere un set di componenti dei prerequisiti da assemblare insieme all'applicazione. Al momento dell'installazione, verrà eseguito un controllo per ogni prerequisito per determinare se esiste già. in caso contrario, verrà installato prima di installare l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione.

 Anziché confezionare e pubblicare prerequisiti, è anche possibile specificare un percorso di download per i componenti. Ad esempio, invece di includere i prerequisiti per ogni applicazione pubblicata, è possibile usare una condivisione file o un percorso Web centralizzato contenente i programmi di installazione per tutti i prerequisiti, in fase di installazione, i componenti verranno scaricati e installati da tale percorso.

> [!IMPORTANT]
> È necessario aggiungere i pacchetti del programma di installazione dei prerequisiti al computer di sviluppo prima di pubblicare la prima [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione. Per altre informazioni, vedere [procedura: includere i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).

 I prerequisiti vengono gestiti nella finestra di dialogo **prerequisiti** , accessibile dal riquadro **pubblica** di **Progettazione progetti**.

> [!NOTE]
> Oltre all'elenco predeterminato dei prerequisiti, è possibile aggiungere componenti personalizzati all'elenco. Per ulteriori informazioni, vedere [creazione di pacchetti del programma di avvio automatico](../deployment/creating-bootstrapper-packages.md).

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Per specificare i prerequisiti per l'installazione di con un'applicazione ClickOnce

1. Con un progetto selezionato in **Esplora soluzioni** , scegliere **proprietà** dal menu **progetto** .

2. Selezionare il riquadro **pubblica** .

3. Fare clic sul pulsante **prerequisiti** per aprire la finestra di dialogo **prerequisiti** .

4. Nella finestra di dialogo **Prerequisiti** verificare che la casella di controllo **Crea programma di installazione per installare componenti dei prerequisiti** sia selezionata.

5. Nell'elenco dei **prerequisiti** selezionare i componenti che si desidera installare, quindi fare clic su **OK**.

     I componenti selezionati verranno inclusi nel pacchetto e pubblicati insieme all'applicazione.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Per specificare un percorso di download diverso per i prerequisiti

1. Con un progetto selezionato in **Esplora soluzioni** , scegliere **proprietà** dal menu **progetto** .

2. Selezionare il riquadro **pubblica** .

3. Fare clic sul pulsante **prerequisiti** per aprire la finestra di dialogo **prerequisiti** .

4. Nella finestra di dialogo **Prerequisiti** verificare che la casella di controllo **Crea programma di installazione per installare componenti dei prerequisiti** sia selezionata.

5. Nella sezione **specificare il percorso di installazione per i prerequisiti** selezionare **Scarica prerequisiti dal percorso seguente**.

6. Selezionare un percorso dall'elenco a discesa oppure immettere un URL, un percorso di file o un percorso FTP, quindi fare clic su **OK.**

    > [!NOTE]
    > È necessario assicurarsi che i programmi di installazione per i componenti specificati esistano nel percorso specificato.

## <a name="see-also"></a>Vedere anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)