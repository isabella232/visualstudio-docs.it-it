---
title: 'Quickstart: Create a Python project from a template in Visual Studio (Guida rapida: Creare un progetto Python da un modello in Visual Studio) | Documenti Microsoft'
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f4b66c5-3ad8-4067-90cd-0100205700a7
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 77e630f7ebfe5739010291ffc62e23a695c40807
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Guida rapida: creare un progetto Python da un modello in Visual Studio

Dopo aver [installato il supporto di Python in Visual Studio 2017](installation.md), è facile creare un nuovo progetto Python con una varietà di modelli.

1. Avviare Visual Studio.

1. Selezionare **File > Nuovo > progetto** (Ctrl+Shift+N). Nel finestra di dialogo **Nuovo progetto**, cercare "Python" e selezionare il modello desiderato. Si noti che la selezione di un modello visualizza una breve descrizione di ciò che offre tale modello. (Vedere anche [Progetti Python](python-projects.md#project-templates)).

    ![Finestra di dialogo VS2017 Nuovo progetto con modelli Python](media/projects-new-project-dialog2.png)

1. Per questa Guida rapida, selezionare il modello "Applicazione Python", assegnare al progetto un nome (ad esempio "MakePI") e un percorso e selezionare **OK**. 

1. Visual Studio crea il file di progetto (un file `.pyproj` su disco) insieme a qualsiasi altro file, come descritto nel modello. Con il modello "Applicazione Python", il progetto contiene un solo file vuoto con lo stesso nome del progetto. Il file è aperto nell'editor di Visual Studio per impostazione predefinita.

    ![Progetto risultante quando si usa il modello di applicazione Python](media/projects-new-structure.png)

1. Aggiungere codice al file aperto, ad esempio il codice seguente che calcola e visualizza le cifre 1000 di PI:

    ```python
    """ Print digits of PI; code adapted from the second, shorter solution
    at http://www.codecodex.com/wiki/Calculate_digits_of_pi#Python
    """

    from time import perf_counter

    def pi_digits_Python(digits):
        scale = 10000
        maxarr = int((digits / 4) * 14)
        arrinit = 2000
        carry = 0
        arr = [arrinit] * (maxarr + 1)
        output = ""

        for i in range(maxarr, 1, -14):
            total = 0
            for j in range(i, 0, -1):
                total = (total * j) + (scale * arr[j])
                arr[j] = total % ((j * 2) - 1)
                total = total / ((j * 2) - 1)

            output += "%04d" % (carry + (total / scale))
            carry = total % scale

        return output;

    def test_py():
        digits = 1000;

        start = perf_counter()
        output = pi_digits_Python(digits);
        elapsed = perf_counter() - start;

        print("PI to " + str(digits) + " digits in " + str(int(elapsed * 10000)/10000) + " seconds:")

        ## replace inserts the decimal point
        print(output.replace("3", "3.", 1))

    if __name__ == "__main__":
        test_py();
    ```

1. Eseguire il programma premendo Ctrl+F5 o selezionando **Debug > Avvia senza eseguire debug** del menu. I risultati vengono visualizzati nella finestra della console.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione: uso di Python in Visual Studio](vs-tutorial-01-01.md)

## <a name="see-also"></a>Vedere anche

- [Creazione di un ambiente per un interprete esistente Python](python-environments.md#creating-an-environment-for-an-existing-interpreter).
- [Installazione del supporto di Python in Visual Studio 2015 e precedenti](installation.md).
- [Percorsi di installazione](installation.md#install-locations).
