---
title: Informazioni di riferimento sulle opzioni degli account
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc3d88fd07ec5d345b3e8697ef69b193ece0fac1
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604904"
---
# <a name="accounts-environment-options-dialog-box"></a>Account, Ambiente, finestra di dialogo Opzioni

Usare questa pagina per impostare varie opzioni correlate agli account usati per accedere a Visual Studio.

## <a name="personalization-account"></a>Account di personalizzazione

### <a name="synchronize-settings-across-devices"></a>Sincronizza le impostazioni in tutti i dispositivi

Usare questa pagina per specificare se sincronizzare o meno le impostazioni in più computer. Per altre informazioni, vedere [Impostazioni sincronizzate](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Abilita il flusso del codice del dispositivo

Quando questa opzione è selezionata, il comportamento di Visual Studio cambia se si seleziona **Aggiungi un account** nella pagina **File** > **Impostazioni account**. Invece della pagina **Accesso all'account**, viene visualizzata una finestra di dialogo in cui sono contenuti un URL e un codice da incollare in un Web browser per eseguire l'accesso. Questa opzione è utile nei casi in cui non è possibile accedere a Visual Studio in modo normale, ad esempio se si usa una versione precedente di Internet Explorer o se il firewall limita l'accesso. Per altre informazioni, vedere l'articolo [Usare più account utente](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Cloud di Azure registrati

Questa sezione illustra le istanze cloud di Azure alle quali si ha accesso tramite uno o più account usati per eseguire l'accesso a Visual Studio. Ad esempio, potrebbe essere possibile accedere a un'istanza privata di Azure nel data center aziendale, oppure a un'istanza di cloud sovrano o per enti pubblici di Azure, ad esempio Azure Cina 21 Vianet o Azure Governo degli Stati Uniti. L'istanza cloud di Azure globale viene visualizzata per impostazione predefinita nell'elenco e non può essere rimossa.

Registrare un cloud di Azure aggiuntivo scegliendo il pulsante **Aggiungi**. Nella finestra di dialogo **Aggiungi nuovo cloud di Azure** sono elencate diverse istanze cloud note di Azure alle quali è possibile connettersi, oppure è possibile immettere l'URL di un endpoint Azure privato.

![Aggiungere un nuova istanza cloud di Azure](media/add-new-azure-cloud.png)

Dopo aver registrato un cloud di Azure aggiuntivo, è possibile scegliere a quale cloud di Azure si vuole accedere quando si esegue l'accesso a Visual Studio.

## <a name="see-also"></a>Vedere anche

- [Sincronizzare le impostazioni tra più computer](../synchronized-settings-in-visual-studio.md)
- [Accedere a Visual Studio](../signing-in-to-visual-studio.md)
- [Usare più account utente](../work-with-multiple-user-accounts.md)
- [Impostazioni dell'ambiente](../environment-settings.md)