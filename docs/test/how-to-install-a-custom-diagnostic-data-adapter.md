---
title: 'Procedura: Installare un adattatore dati di diagnostica personalizzato in Visual Studio'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, installing
ms.assetid: 907e65d8-0408-44b3-9e5e-e631892c1726
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9d2d6c30696636bc8fd2ca571940ac0165eabbcf
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44321047"
---
# <a name="how-to-install-a-custom-diagnostic-data-adapter"></a>Procedura: Installare un adattatore dati di diagnostica personalizzato

Se si è creato un adattatore dati di diagnostica personalizzato o si è ricevuto un adattatore dati di diagnostica personalizzato da utilizzare, è possibile installare l'assembly dell'adattatore dati di diagnostica copiando il relativo file di assembly nella directory corretta sul computer locale.

 Se si desidera utilizzare l'adattatore dati di diagnostica personalizzato per un ruolo in un ambiente, è necessario installare l'adattatore dati di diagnostica in tutti i computer che eseguono agenti di test utilizzabili per questo ruolo.

 Utilizzare la procedura riportata di seguito per installare l'adattatore diagnostico personalizzato nei percorsi appropriati. Saranno necessarie le autorizzazioni amministrative in tutti i computer in cui si installa l'adattatore dati di diagnostica.

## <a name="install-a-custom-diagnostic-data-adapter"></a>Installare un adattatore dati di diagnostica personalizzato

### <a name="to-install-a-custom-diagnostic-data-adapter"></a>Per installare un adattatore dati di diagnostica personalizzato

1.  Per usare l'adattatore dati di diagnostica quando si eseguono test nel computer client o in un computer agente, copiare tutti i file dalla directory di compilazione alla directory seguente nel computer di destinazione, in base al percorso di installazione:

     *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*

     I file da copiare sono i seguenti:

    -   Assembly dell'adattatore dati di diagnostica (*DLL*) (obbligatorio).

    -   File di dati di debug (*PDB*) per l'adattatore (facoltativo).

    -   File di configurazione per l'adattatore (`<diagnostic data adapter name>.dll.config`), se sono presenti impostazioni di configurazione predefinite (facoltativo).

    -   Assembly dell'editor di configurazione, se ne è stato creato uno per modificare le impostazioni di configurazione per l'adattatore (facoltativo). Questo file è solo per i computer client. I computer agente non utilizzano l'editor.

    > [!NOTE]
    > Anche se l'adattatore dati di diagnostica e l'editor di configurazione possono essere creati nello stesso progetto e compilati nello stesso assembly, è possibile utilizzare progetti distinti e creare assembly distinti, se lo si preferisce.

     Per altre informazioni sulla configurazione delle impostazioni test per usare un ambiente quando si eseguono i test, vedere [Raccogliere dati di diagnostica nei test manuali (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

2.  Per selezionare l'adattatore dati di diagnostica per un test, è necessario in primo luogo selezionare impostazioni test esistenti o crearne di nuove da Microsoft Test Manager o Visual Studio, quindi selezionare l'adattatore dati di diagnostica nella scheda **Dati e diagnostica** delle impostazioni di test selezionate.

3.  Se è stato creato e installato un editor di configurazione dell'adattatore dati di diagnostica, per configurare l'adattatore dati di diagnostica per le impostazioni test scegliere **Configura** accanto all'adattatore e apportare le modifiche. Quindi, scegliere **Salva**. Per altre informazioni su come creare un editor di configurazione per l'agente di raccolta dati di diagnostica, vedere [Procedura: Creare un editor personalizzato di dati per l'adattatore dati di diagnostica](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md).

4.  Se i test vengono eseguiti da Microsoft Test Manager, è possibile assegnare queste impostazioni test al piano di test prima di eseguire i test oppure usare il comando **Esegui con opzioni** per assegnare impostazioni test ed eseguire l'override delle impostazioni test. Per altre informazioni sulle impostazioni test, vedere [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

     Se i test vengono eseguiti da Visual Studio, è necessario impostare come attive queste impostazioni di test. Per altre informazioni sulle impostazioni test, vedere [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

5.  Eseguire i test utilizzando le impostazioni di test con l'adattatore dati di diagnostica selezionato.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare un adattatore dati di diagnostica](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Procedura: Creare un editor personalizzato di dati per l'adattatore dati di diagnostica](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Esempio di progetto per creare un adattatore dati di diagnostica](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Creare un adattatore dati di diagnostica per raccogliere dati personalizzati o influire su un computer di test](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)