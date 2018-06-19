---
title: Risolvere i problemi di caricamento dei modelli di progetto e dei modelli di elemento di Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4bb6a10e92bf8f26ffbcb81796b3c5c8371600b5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943319"
---
# <a name="how-to-troubleshoot-templates"></a>Procedura: Risolvere i problemi relativi ai modelli

Se un modello non viene caricato nell'ambiente di sviluppo, sono disponibili diversi metodi per individuare il problema.

## <a name="validate-the-vstemplate-file"></a>Convalidare il file con estensione vstemplate

Se il file con estensione *vstemplate* di un modello non rispetta lo schema di modello di Visual Studio, è possibile che il modello non venga visualizzato nella finestra di dialogo **Nuovo progetto**.

### <a name="to-validate-the-vstemplate-file"></a>Per convalidare il file con estensione vstemplate

1. Individuare il file con estensione *zip* che contiene il modello.

1. Estrarre il file con estensione *zip*.

1. Nel menu **File** di Visual Studio scegliere **Apri** > **File**.

1. Selezionare il file con estensione *vstemplate* per il modello e scegliere **Apri**.

1. Verificare che il codice XML del file con estensione *vstemplate* rispetti lo schema del modello. Per altre informazioni sullo schema del file con estensione *vstemplate*, vedere [Riferimenti allo schema dei modelli](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Per ottenere il supporto IntelliSense durante la creazione del file con estensione *vstemplate*, aggiungere un attributo `xmlns` all'elemento `VSTemplate` e assegnare all'attributo il valore http://schemas.microsoft.com/developer/vstemplate/2005.

1. Salvare e chiudere il file con estensione *vstemplate*.

1. Selezionare i file inclusi nel modello, fare clic con il pulsante destro del mouse e selezionare **Invia a** > **Cartella compressa**. I file selezionati verranno compressi in un file con estensione *zip*.

1. Inserire il nuovo file *zip* nella stessa directory del file *zip* precedente.

1. Eliminare i file di modello estratti e il file di modello precedente con estensione *zip*.

## <a name="enable-diagnostic-logging"></a>Abilitare la registrazione diagnostica

È possibile abilitare la registrazione diagnostica per l'individuazione dei modelli seguendo la procedura in [Risoluzione dei problemi di individuazione dei modelli (estendibilità)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Vedere anche

- [Risoluzione dei problemi di individuazione dei modelli (estendibilità)](../extensibility/troubleshooting-template-discovery.md)
- [Personalizzare i modelli](../ide/customizing-project-and-item-templates.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Riferimento allo schema di modello](../extensibility/visual-studio-template-schema-reference.md)