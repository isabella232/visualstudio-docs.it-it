---
title: Distribuzione VSIX di un linguaggio DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916552"
---
# <a name="vsix-deployment-of-a-dsl"></a>Distribuzione VSIX di un linguaggio DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile installare un linguaggio specifico di dominio nel computer in uso o in altri computer. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] necessario che sia già installato nel computer di destinazione.

## <a name="Installing"></a>Installazione e disinstallazione di un linguaggio DSL tramite il VSX
 Quando il linguaggio DSL viene installato da questo metodo, l'utente può aprire un file DSL dall'interno [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ma il file non può essere aperto da Esplora risorse.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>Per installare un linguaggio DSL usando il progetto VSIX

1. Nel computer trovare il file **. vsix** compilato dal progetto di pacchetto DSL.

    1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **DslPackage** , quindi scegliere **Apri cartella in Esplora risorse**.

    2. Individuare il file **bin\\\*\\** _progettoutente_ **. DslPackage. vsix**

2. Copiare il file **VSIX** nel computer di destinazione in cui si vuole installare il linguaggio DSL. Può trattarsi del computer in uso o di un altro computer.

    - Il computer di destinazione deve avere una delle edizioni di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] che supporta DSLs in fase di esecuzione. Per altre informazioni, vedere le [edizioni di Visual Studio supportate per la visualizzazione & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - Il computer di destinazione deve avere una delle edizioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] specificate in **DslPackage\source.Extensions.manifest**.

3. Nel computer di destinazione fare doppio clic sul file **VSIX** .

     **Visual Studio Extension Installer** si apre e installa l'estensione.

4. Avviare o riavviare [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

5. Per testare il linguaggio DSL, usare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per creare un nuovo file con l'estensione definita per il linguaggio DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Per disinstallare un linguaggio DSL installato tramite VSX

1. Scegliere **Gestione estensioni**dal menu **strumenti** .

2. Espandere **Estensioni installate**.

3. Selezionare l'estensione in cui è definito il linguaggio DSL, quindi fare clic su **Disinstalla**.

   Raramente, un'estensione errata non viene caricata e crea un report nella finestra degli errori, ma non viene visualizzata in Gestione estensioni. In tal caso, è possibile rimuovere l'estensione eliminando il file da:

   **\Microsoft\VisualStudio\10.0\Extensions** LocalAppData
