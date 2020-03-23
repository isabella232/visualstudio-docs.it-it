---
title: Informazioni di riferimento sulle opzioni degli account
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ff457523024db49502ae982a390d9a7be6ba9dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595904"
---
# <a name="accounts-environment-options-dialog-box"></a>Account, Ambiente, finestra di dialogo Opzioni

Usare questa pagina per impostare varie opzioni correlate agli account usati per accedere a Visual Studio.

## <a name="personalization-account"></a>Account di personalizzazione

### <a name="synchronize-settings-across-devices"></a>Sincronizza le impostazioni in tutti i dispositivi

Usare questa pagina per specificare se sincronizzare o meno le impostazioni in più computer. Per altre informazioni, vedere [Impostazioni sincronizzate](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Abilita il flusso del codice del dispositivo

Quando questa opzione è selezionata, il comportamento di Visual Studio cambia se si seleziona **Aggiungi un account** nella pagina **File** > **Impostazioni account**. Invece della pagina **Accesso all'account**, viene visualizzata una finestra di dialogo in cui sono contenuti un URL e un codice da incollare in un Web browser per eseguire l'accesso. Questa opzione è utile nei casi in cui non è possibile accedere a Visual Studio in modo normale, ad esempio se si usa una versione precedente di Internet Explorer o se il firewall limita l'accesso. Per altre informazioni, vedere l'articolo [Usare più account utente](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Cloud di Azure registrati

Questa sezione illustra le istanze cloud di Azure alle quali si ha accesso tramite uno o più account usati per eseguire l'accesso a Visual Studio. Ad esempio, potrebbe essere possibile accedere a un'istanza privata di Azure nel data center aziendale, In alternativa, è possibile avere accesso a un'istanza di Azure sovrana o governativa, ad esempio Azure China 21 Vianet o Azure U.S. Government.Or, you might have access to a sovereign or government instance of Azure such as Azure China 21 Vianet or Azure U.S. Government. L'istanza cloud di Azure globale viene visualizzata per impostazione predefinita nell'elenco e non può essere rimossa.

Registrare un cloud di Azure aggiuntivo scegliendo il pulsante **Aggiungi**. Nella finestra di dialogo **Aggiungi nuovo cloud di Azure** sono elencate diverse istanze cloud note di Azure alle quali è possibile connettersi, oppure è possibile immettere l'URL di un endpoint Azure privato.

![Aggiungere un nuova istanza cloud di Azure](media/add-new-azure-cloud.png)

Dopo aver registrato un cloud di Azure aggiuntivo, è possibile scegliere a quale cloud di Azure si vuole accedere quando si esegue l'accesso a Visual Studio.

## <a name="see-also"></a>Vedere anche

- [Sincronizzare le impostazioni tra più computer](../synchronized-settings-in-visual-studio.md)
- [Accesso a Visual Studio](../signing-in-to-visual-studio.md)
- [Usare più account utente](../work-with-multiple-user-accounts.md)
- [Impostazioni di ambiente](../environment-settings.md)
