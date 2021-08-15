---
title: Utilizzare gli account GitHub in Visual Studio
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: Informazioni su come usare i Visual Studio con GitHub account.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 8057132db3d547627debbed87e7e4827b251028f3dfbeb8f86b870a9e098e3a0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121258304"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Utilizzare gli account GitHub in Visual Studio

Se si dispone di un account GitHub o GitHub Enterprise, è possibile aggiungerlo al keychain Visual Studio pubblico. Dopo aver aggiunto l'account, sarà possibile sfruttare l'integrazione della piattaforma accedendo e creando repository GitHub, direttamente da Visual Studio.

## <a name="adding-public-github-accounts"></a>Aggiunta di account GitHub pubblici

È possibile aggiungere l'account GitHub pubblico se è già stato eseguito l'accesso a Visual Studio con un account account Microsoft o aziendale o dell'istituto di istruzione.

1. Selezionare l'icona con le proprie iniziali nell'angolo superiore destro dell'Visual Studio virtuale. Selezionare quindi **Impostazioni account per** gestire gli account. È anche possibile aprire la finestra di Impostazioni account selezionando **Account**  >  **file Impostazioni**.

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Impostazioni account":::

2. Nel sottomenu **Tutti gli** account selezionare il segno più per aggiungere un account e selezionare **GitHub**.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="Selezionare Aggiungi GitHub account":::

3. Si verrà reindirizzati al browser, in cui è possibile accedere con le credenziali GitHub utente. Dopo l'accesso, verrà visualizzata una finestra di operazione riuscita nel browser ed è possibile tornare a Visual Studio.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Finestra operazione riuscita nel browser":::

4. Entrambi gli account saranno presenti nel sottomenu **Tutti gli** account.

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Visualizzazione di entrambi gli account":::

Se non è già stato eseguito l'accesso a Visual Studio  con un account diverso, selezionare il collegamento Accedi nell'angolo superiore destro dell'ambiente Visual Studio dati. È anche possibile aprire la finestra di Impostazioni account selezionando **Account**  >  **file Impostazioni**. Seguire quindi le istruzioni precedenti per aggiungere l'account GitHub personale.

![Utente non connesso](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>Aggiunta GitHub account aziendali

Per impostazione predefinita, Visual Studio sono abilitati solo account GitHub pubblici.

1. Per abilitare GitHub account aziendali, passare a **Strumenti**  >  **Opzioni** e cercare le **opzioni** Account.

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Menu delle opzioni account":::

2. Selezionare quindi la casella Includi account **GitHub Enterprise Server**. La volta successiva che si passa **all'Impostazioni** account e si prova ad aggiungere un account GitHub, verranno visualizzati le opzioni per GitHub e GitHub Enterprise.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="Accedere con GitHub Enterprise":::

3. Dopo aver immesso l GitHub Enterprise del server di destinazione, **selezionare Accedi con il browser.** Qui è possibile accedere usando le credenziali GitHub Enterprise utente.

## <a name="see-also"></a>Vedi anche

- [Gestire più account utente](work-with-multiple-user-accounts.md)
- [Accedi a Visual Studio](signing-in-to-visual-studio.md)
