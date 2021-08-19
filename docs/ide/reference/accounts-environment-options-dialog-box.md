---
title: Informazioni di riferimento sulle opzioni degli account
description: Informazioni su come impostare alcune opzioni relative agli account che si usano quando si accede a Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 9fb7def00f37a8f396de37d644ab826a412250ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062368"
---
# <a name="accounts-environment-options-dialog-box"></a>Account, Ambiente, finestra di dialogo Opzioni

Usare questa pagina per impostare varie opzioni correlate agli account usati per accedere a Visual Studio.

## <a name="personalization-account"></a>Account di personalizzazione

### <a name="synchronize-settings-across-devices"></a>Sincronizza le impostazioni in tutti i dispositivi

Usare questa pagina per specificare se sincronizzare o meno le impostazioni in più computer. Per altre informazioni, vedere [Impostazioni sincronizzate](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Abilita il flusso del codice del dispositivo

Quando questa opzione è selezionata, il comportamento di Visual Studio cambia se si seleziona **Aggiungi un account** nella pagina **File** > **Impostazioni account**. Invece della pagina **Accesso all'account**, viene visualizzata una finestra di dialogo in cui sono contenuti un URL e un codice da incollare in un Web browser per eseguire l'accesso. Questa opzione è utile nei casi in cui non è possibile accedere a Visual Studio in modo normale, ad esempio se si usa una versione precedente di Internet Explorer o se il firewall limita l'accesso. Per altre informazioni, vedere l'articolo [Usare più account utente](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Cloud di Azure registrati

Questa sezione illustra le istanze cloud di Azure alle quali si ha accesso tramite uno o più account usati per eseguire l'accesso a Visual Studio. Ad esempio, potrebbe essere possibile accedere a un'istanza privata di Azure nel data center aziendale, Oppure si potrebbe avere accesso a un'istanza sovrana o governativa di Azure, ad esempio Azure Cina 21 Vianet o Azure U.S. Government. L'istanza cloud di Azure globale viene visualizzata per impostazione predefinita nell'elenco e non può essere rimossa.

Registrare un cloud di Azure aggiuntivo scegliendo il pulsante **Aggiungi**. Nella finestra di dialogo **Aggiungi nuovo cloud di Azure** sono elencate diverse istanze cloud note di Azure alle quali è possibile connettersi, oppure è possibile immettere l'URL di un endpoint Azure privato.

![Aggiungere un nuova istanza cloud di Azure](media/add-new-azure-cloud.png)

Dopo aver registrato un cloud di Azure aggiuntivo, è possibile scegliere a quale cloud di Azure si vuole accedere quando si esegue l'accesso a Visual Studio.

## <a name="see-also"></a>Vedi anche

- [Sincronizzare le impostazioni tra più computer](../synchronized-settings-in-visual-studio.md)
- [Accedi a Visual Studio](../signing-in-to-visual-studio.md)
- [Gestire più account utente](../work-with-multiple-user-accounts.md)
- [Impostazioni dell'ambiente](../environment-settings.md)
