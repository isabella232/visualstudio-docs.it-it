---
title: Utilizzare gli account GitHub in Visual Studio
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: Informazioni su come usare Visual Studio con GitHub account.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 8d175297f866ed09c00fcc38b635ab1c071f4284
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077933"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Utilizzare gli account GitHub in Visual Studio

Se si ha un account GitHub o GitHub Enterprise, è possibile aggiungerlo al keychain Visual Studio personale. Dopo aver aggiunto l'account, sarà possibile sfruttare l'integrazione della piattaforma accedendo e creando GitHub repository, direttamente da Visual Studio.

## <a name="adding-public-github-accounts"></a>Aggiunta di account GitHub pubblici

È possibile aggiungere l'account GitHub pubblico se è già stato eseguito l'accesso a Visual Studio con un account account Microsoft o aziendale o dell'istituto di istruzione.

1. Selezionare l'icona con le iniziali nell'angolo superiore destro dell'Visual Studio locale. Selezionare quindi **Impostazioni account per** gestire gli account. È anche possibile aprire la finestra di Impostazioni account selezionando **Account**  >  **file Impostazioni**.

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Impostazioni account":::

2. Nel sottomenu **Tutti gli account** selezionare il segno più per aggiungere un account e selezionare GitHub . 

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="Selezionare Aggiungi GitHub account":::

3. Si verrà reindirizzati al browser, in cui è possibile accedere con le proprie GitHub credenziali. Dopo l'accesso, si otterrà una finestra di esito positivo nel browser ed è possibile tornare a Visual Studio.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Finestra Operazione riuscita nel browser":::

4. Entrambi gli account saranno presenti nel sottomenu **Tutti gli** account.

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Entrambi gli account mostrano":::

Se non si è già connessi a Visual Studio con un  account diverso, selezionare il collegamento Accedi nell'angolo superiore destro dell'ambiente Visual Studio locale. È anche possibile aprire la finestra di Impostazioni account selezionando **Account**  >  **file Impostazioni**. Seguire quindi le istruzioni precedenti per aggiungere l'account GitHub locale.

![Utente non connesso](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>Aggiunta GitHub account aziendali

Per impostazione predefinita, Visual Studio sono abilitati solo account GitHub pubblici.

1. Per abilitare GitHub account aziendali, passare a **Opzioni** degli strumenti  >   e cercare le **opzioni** Account.

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Menu delle opzioni account":::

2. Selezionare quindi la casella Includi **account GitHub Enterprise Server**. La volta successiva che si passa a **Account Impostazioni** e si prova ad aggiungere un account GitHub, verranno visualizzati le opzioni sia per GitHub che per GitHub Enterprise.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="Accedere con GitHub Enterprise":::

3. Dopo aver immesso l'GitHub Enterprise server, selezionare **Accedi con il browser.** Qui è possibile accedere usando le credenziali GitHub Enterprise utente.

## <a name="see-also"></a>Vedi anche

- [Gestire più account utente](work-with-multiple-user-accounts.md)
- [Accedi a Visual Studio](signing-in-to-visual-studio.md)
