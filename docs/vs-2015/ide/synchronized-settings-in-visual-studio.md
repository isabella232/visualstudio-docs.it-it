---
title: Impostazioni sincronizzate in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e0facac569671c880004d1fc1a7aa29487e7926
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531032"
---
# <a name="synchronized-settings-in-visual-studio"></a>Impostazioni sincronizzate in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [sincronizzare le impostazioni in Visual Studio](https://docs.microsoft.com/visualstudio/ide/synchronized-settings-in-visual-studio).  
  
Per impostazione predefinita, quando si usa lo stesso account di personalizzazione per accedere a Visual Studio Online da più computer, le impostazioni vengono sincronizzate su tutti i computer.  
  
## <a name="synchronized-settings"></a>Impostazioni sincronizzate  
 Per impostazione predefinita, vengono sincronizzate le impostazioni seguenti.  
  
-   Impostazioni di sviluppo. È necessario selezionare un set di impostazioni la prima volta che si esegue Visual Studio, ma è possibile modificare la selezione in qualsiasi momento. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
-   Le opzioni seguenti nelle pagine **Strumenti &#124; Opzioni**:  
  
    -   Impostazioni del **tema** e di maiuscole e minuscole nella barra dei menu nella pagina delle opzioni **Ambiente**, **Generale**  
  
    -   Tutte le impostazioni nella pagina delle opzioni **Ambiente**, **Tipi di carattere e colori**  
  
    -   Tutti i tasti di scelta rapida nella pagina delle opzioni **Ambiente**, **Tastiera**  
  
    -   Tutte le impostazioni nella pagina delle opzioni **Ambiente, Schede e Finestre**  
  
    -   Tutte le impostazioni nella pagina delle opzioni **Ambiente**, **Avvio**  
  
    -   Tutte le impostazioni nelle pagine delle opzioni **Editor di testo**  
  
-   Tutte le impostazioni nelle pagine delle opzioni di XAML Designer  
  
-   Alias di comandi definiti dall'utente. Per altre informazioni su come definire gli alias di comandi, vedere [Alias di comandi di Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
-   I layout delle finestre definite dall'utente nella pagina **Finestra &#124; Gestisci layout finestra**  
  
## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>Disattivazione delle impostazioni sincronizzate per un computer particolare  
 Le impostazioni sincronizzate per Visual Studio sono attivate per impostazione predefinita. È possibile disattivare le impostazioni sincronizzate in un computer visitando la pagina **Strumenti &#124; Opzioni &#124; Ambiente&#124; Impostazioni sincronizzate** e deselezionando la casella di controllo.  Se, ad esempio, si decide di non sincronizzare le impostazioni di Visual Studio nel computer A, nessuna delle modifiche alle impostazioni del computer A verrà visualizzata nel computer B o nel computer C. I computer B e C continueranno a sincronizzarsi tra di loro, ma non si sincronizzeranno con il computer A.  
  
## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Impostazioni di sincronizzazione tra prodotti e edizioni della famiglia Visual Studio  
 Le impostazioni possono essere sincronizzate tra tutte le edizioni di Visual Studio 2015, comprese le edizioni Express e Community. Le impostazioni vengono sincronizzate anche tra prodotti della famiglia Visual Studio, come ad esempio Blend. Tuttavia, ogni prodotto di questa famiglia potrebbe disporre di impostazioni personalizzate che non vengono condivise con Visual Studio. Ad esempio, impostazioni specifiche per Blend sul Computer A verranno condivise con Blend sul Computer B, ma non con Visual Studio sul Computer A o B.  
  
> [!WARNING]
>  Le impostazioni non vengono sincronizzate tra Visual Studio 2013 e Visual Studio 2015. Alla prima apertura di Visual Studio 2015 le impostazioni di Visual Studio 2013 vengono migrate, ma non possono essere migrate di nuovo in Visual Studio 2013 dopo questa operazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione dell'IDE](../ide/personalizing-the-visual-studio-ide.md)



