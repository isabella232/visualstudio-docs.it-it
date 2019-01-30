---
title: Informazioni di riferimento sulle opzioni degli account
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00b99a75579f63dd19de74c6d5bc3c13a2833bc3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996116"
---
# <a name="accounts-environment-options-dialog-box"></a>Account, Ambiente, finestra di dialogo Opzioni

Usare questa pagina per impostare varie opzioni correlate agli account usati per accedere a Visual Studio.

## <a name="personalization-account"></a>Account di personalizzazione

### <a name="synchronize-settings-across-devices"></a>Sincronizza le impostazioni in tutti i dispositivi

Usare questa pagina per specificare se sincronizzare o meno le impostazioni in più computer. Per altre informazioni, vedere [Impostazioni sincronizzate](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Abilita il flusso del codice del dispositivo

Quando questa opzione è selezionata, il comportamento di Visual Studio cambia se si seleziona **Aggiungi un account** nella pagina **File** > **Impostazioni account**. Invece della pagina **Accesso all'account**, viene visualizzata una finestra di dialogo in cui sono contenuti un URL e un codice da incollare in un Web browser per eseguire l'accesso. Questa opzione è utile nei casi in cui non è possibile accedere a Visual Studio in modo normale, ad esempio se si usa una versione precedente di Internet Explorer o se il firewall limita l'accesso. Per altre informazioni, vedere l'articolo [Usare più account utente](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Cloud di Azure registrati

Questa sezione illustra le istanze cloud di Azure alle quali si ha accesso tramite uno o più account usati per eseguire l'accesso a Visual Studio. Ad esempio, potrebbe essere possibile accedere a un'istanza privata di Azure nel data center aziendale, oppure a un'istanza di cloud sovrano o governativo di Azure, ad esempio Azure Cina o Azure Governo degli Stati Uniti. L'istanza cloud di Azure globale viene visualizzata per impostazione predefinita nell'elenco e non può essere rimossa.

Registrare un cloud di Azure aggiuntivo scegliendo il pulsante **Aggiungi**. Nella finestra di dialogo **Aggiungi nuovo cloud di Azure** sono elencate diverse istanze cloud note di Azure alle quali è possibile connettersi, oppure è possibile immettere l'URL di un endpoint Azure privato.

![Aggiungere un nuova istanza cloud di Azure](media/add-new-azure-cloud.png)

Dopo aver registrato un cloud di Azure aggiuntivo, è possibile scegliere a quale cloud di Azure si vuole accedere quando si esegue l'accesso a Visual Studio.

## <a name="see-also"></a>Vedere anche

- [Sincronizzare le impostazioni tra più computer](../synchronized-settings-in-visual-studio.md)
- [Accedere a Visual Studio](../signing-in-to-visual-studio.md)
- [Usare più account utente](../work-with-multiple-user-accounts.md)
- [Impostazioni dell'ambiente](../environment-settings.md)
- [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)