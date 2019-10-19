---
title: 'Procedura: Configurare progetti per le piattaforme di destinazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6ba899fd1b17fa5a82c64d5c5e44e67f0d5eb97
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668197"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Procedura: configurare progetti per le piattaforme di destinazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di configurare le applicazioni per diverse piattaforme di destinazione, tra cui le piattaforme a 64 bit. Per altre informazioni sul supporto delle piattaforme a 64 bit in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vedere [Applicazioni a 64 bit](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).

## <a name="targeting-platforms-with-the-configuration-manager"></a>Individuazione delle piattaforme di destinazione con Gestione configurazione
 La **Gestione configurazione** consente di aggiungere rapidamente una nuova piattaforma di destinazione al progetto. Se si seleziona una delle piattaforme incluse con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], le proprietà del progetto vengono modificate per compilare il progetto per la piattaforma selezionata.

#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Per configurare un progetto per una piattaforma a 64 bit

1. Nella barra dei menu scegliere **Compilazione**, **Gestione configurazione**.

2. Nell'elenco **Piattaforma soluzione attiva** scegliere una piattaforma a 64 bit di destinazione per la soluzione e quindi scegliere il pulsante **Chiudi**.

   1. Se la piattaforma non compare nell'elenco **Piattaforma soluzione attiva**, scegliere **Nuova**.

        Viene visualizzata la finestra di dialogo **Nuova piattaforma soluzione**.

   2. Nell'elenco **Digitare o selezionare la nuova piattaforma** scegliere **x64**.

       > [!NOTE]
       > Se si specifica un nuovo nome per la configurazione, potrebbe essere necessario modificare le impostazioni in **Creazione progetti** per la piattaforma corretta.

   3. Se si vuole copiare le impostazioni da una configurazione di piattaforma corrente, selezionarla e quindi fare clic sul pulsante **OK**.

   Le proprietà per tutti i progetti destinati alla piattaforma a 64 bit vengono aggiornate e la compilazione successiva del progetto verrà ottimizzata per le piattaforme a 64 bit.

## <a name="targeting-platforms-in-the-project-designer"></a>Individuazione delle piattaforme di destinazione in Progettazione progetti
 Anche Progettazione progetti consente di creare diverse piattaforme di destinazione per il progetto. Se la selezione di una delle piattaforme incluse nell'elenco della finestra di dialogo **Nuova piattaforma soluzione** non è applicabile alla soluzione, è possibile creare un nome di configurazione personalizzato e modificare le impostazioni in **Creazione progetti** per la piattaforma di destinazione corretta.

 L'esecuzione di questa attività varia in base al linguaggio di programmazione usato. Per altre informazioni, vedere i collegamenti che seguono:

- Per i progetti [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], vedere [/platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).

- Per i progetti [!INCLUDE[csprcs](../includes/csprcs-md.md)], vedere [Pagina Compilazione, Creazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Per i progetti [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], vedere [/clr (Compilazione Common Language Runtime)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).

## <a name="see-also"></a>Vedere anche
 [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md) [/Platform (C# opzioni del compilatore)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04) [applicazioni a 64 bit](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181) [Visual Studio IDE supporto per 64 bit](../ide/visual-studio-ide-64-bit-support.md)
