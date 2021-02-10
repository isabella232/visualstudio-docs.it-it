---
title: Utilizzare gli account GitHub in Visual Studio
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: Informazioni su come usare Visual Studio con gli account GitHub.
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9da0f2c2df796f50530f19252c7236c2bb606a10
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960481"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Utilizzare gli account GitHub in Visual Studio

Se si dispone di un account GitHub pubblico o GitHub aziendale, è possibile aggiungerlo al keychain di Visual Studio. Dopo aver aggiunto l'account, sarà possibile sfruttare l'integrazione della piattaforma accedendo e creando repository GitHub direttamente da Visual Studio.

## <a name="adding-public-github-accounts"></a>Aggiunta di account GitHub pubblici

È possibile aggiungere l'account GitHub pubblico se è già stato effettuato l'accesso a Visual Studio con una account Microsoft o un account aziendale o dell'Istituto di istruzione.

1. Selezionare l'icona con le iniziali nell'angolo superiore destro dell'ambiente Visual Studio. Quindi, selezionare **Impostazioni account...** per gestire gli account. Per aprire la finestra di dialogo Impostazioni account, è anche possibile passare a **file**  >  **Impostazioni account**.

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Impostazioni account":::

2. Nel sottomenu **tutti gli account** selezionare il segno più per aggiungere un account e selezionare **GitHub**.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="Selezionare Aggiungi account GitHub":::

3. Si verrà reindirizzati al browser, in cui è possibile accedere con le credenziali di GitHub. Dopo aver eseguito l'accesso, si otterrà una finestra di operazione riuscita nel browser ed è possibile tornare a Visual Studio.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Finestra di operazione riuscita nel browser":::

4. Entrambi gli account saranno presenti nel sottomenu **tutti gli account** .

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Entrambi gli account che mostrano":::

Se non è già stato effettuato l'accesso a Visual Studio con un account diverso, selezionare il collegamento **Accedi** nell'angolo superiore destro dell'ambiente Visual Studio. Per aprire la finestra di dialogo Impostazioni account, è anche possibile passare a **file**  >  **Impostazioni account**. Quindi, seguire le istruzioni riportate sopra per aggiungere l'account GitHub.

![Utente non connesso](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>Aggiunta di account di GitHub Enterprise

Per impostazione predefinita, in Visual Studio sono abilitati solo account GitHub pubblici.

1. Per abilitare gli account di GitHub Enterprise, passare a **strumenti**  >  **Opzioni** e cercare le opzioni per gli **account** .

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Menu Opzioni account":::

2. Selezionare quindi la casella per **includere gli account github Enterprise Server**. La volta successiva che si passa alle **impostazioni dell'account** e si tenta di aggiungere un account github, verranno visualizzate le opzioni per GitHub e GitHub Enterprise.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="Accedi con GitHub Enterprise":::

3. Dopo aver immesso l'indirizzo di GitHub Enterprise Server, selezionare **Accedi con il browser**. In questa pagina è possibile accedere usando le credenziali aziendali di GitHub.

## <a name="see-also"></a>Vedi anche

- [Gestire più account utente](work-with-multiple-user-accounts.md)
- [Accedi a Visual Studio](signing-in-to-visual-studio.md)
