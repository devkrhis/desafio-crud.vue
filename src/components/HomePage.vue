<template>
    <div id="homePage">
        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
        <link href="https://fonts.googleapis.com/css2?family=Kanit&display=swap" rel="stylesheet">
        <table id="bordMagic">
            <tr id="NomenclaturaEditaveis"> 
                <td> ID </td>
                <td> Nome </td>
                <td> Idade </td>
                <td> Cep </td>
                <td> Cidade </td>
                <td> Estado </td>
                <td> Editar Item</td>
                <td> Deletar Item</td>
            </tr>
            
            <tr id="itemsEditaveis" v-for="items in myListArray" :key="items.key">
                <td> {{ items.id }}</td>
                <td> {{ items.nome }}</td>
                <td> {{ items.idade }}</td>
                <td> {{ items.Local.cep }}</td>
                <td> {{ items.Local.cidade }}</td>
                <td> {{ items.Local.estado }}</td>
                <td> <button type="button" @click="editObject(items.id)"> Edit Object</button> </td>
                <td> <button type="button" @click="deletAll(items.id)"> Delet Object</button> </td>
            </tr>
            <hr>
            <div id="foraDoEscopo">
            <button type="button" @click="addNewItem"> Add New Item</button>
            <button type="button" @click="DoubleAge"> Multiplier Age</button>
            </div>
        </table>

    </div>
    
</template>

<script>
/* eslint-disable */
export default {
    data(){
        return {
            numberRandom: 3,
            myListArray: [
                {
                    id: 1,
                    nome: "Krhistopher",
                    idade: 25,
                    Local: {
                        cep: 83405310,
                        cidade: "Colombo",
                        estado: "Paraná"
                    }
                },
                {
                    id: 2,
                    nome: "Jose",
                    idade: 70,
                    Local: {
                        cep: 8323232010,
                        cidade: "Joinvile",
                        estado: "Santa catarina"
                    }
                },
                {
                    id: 3,
                    nome: "Isadora",
                    idade: 101,
                    Local: {
                        cep: 1231323123,
                        cidade: "Smallvile",
                        estado: "Gasoso"
                    }
                }
            ]
        }
    },
    methods: {
        addNewItem(){
            this.numberRandom++
            let newItem = {
                id: this.numberRandom,
                nome: "Isadora",
                idade: 101,
                Local: {
                    cep: 1231323123,
                    cidade: "Smallvile",
                    estado: "Gasoso"
                    } 
            }
            this.myListArray.push(newItem)
        }, 
        DoubleAge(){
            // essa funcao vai duplicar todas as minhas idades por 2
            console.log("Estou multiplicando todas as idades por * 2")
            
            const doubleNumber = this.myListArray.map((numbersDouble, index) => {
                console.log(numbersDouble.idade *= 2)
                return numbersDouble.idade *= 2
            })
            this.myListArray.idade = doubleNumber
        },
        editObject(event){
            
            console.log("Passei pelo evento do click:", event)

            const numbersArray = this.myListArray

            const elementName = numbersArray.findIndex((getDadosArray) => {
                return getDadosArray.id == event
            })
            console.log("Passei pelo elementName", elementName)
            
            this.myListArray[elementName].nome = "Krhistopher"
            

        },
        deletAll(event){
           const positionId = event
           console.log(positionId)

           const numbersArray = this.myListArray // recebendo meu array inteiro
           console.log(numbersArray)

           const elementIndex = numbersArray.findIndex((getDadosArray) => { // procurando os dados e fazendo uma validação se o click do mouse é a mesma posição do meu index.
            console.log("passei aqui no position id", positionId)
            return getDadosArray.id == positionId
           });

           console.log("passei aqui no element Index", elementIndex)
           this.myListArray.splice(elementIndex, 1) // removendo o elemento que eu quero
            

        }
    }
}
</script>

<style scoped>

#bordMagic{
    border: 3px solid black;
    padding: 0px 0px 0px 0px;
    font-family: 'Kanit', sans-serif;

}

#NomenclaturaEditaveis{
    background-color: rgba(0, 0, 0, 0.63);
    color: white;
}

#itemsEditaveis {
    background-color: rgba(0, 0, 0, 0.863);
    color: white;
}

#bordMagic td button {
    background-color: rgba(255, 255, 255, 0.397);
    border: 2px solid white;
    padding: 10px;
    color: white;
}

#bordMagic td button:hover{
    border: 2px solid rgb(255, 0, 0);
    background-color: red;

}

#bordMagic td {
    border: 0px solid black;
    padding: 5px 40px 30px 5px;
}

hr {
    border: 1px solid black;
}

#foraDoEscopo button {
    background-color: rgba(0, 0, 0, 0.205);
    border: 2px solid rgb(0, 0, 0);
    padding: 20px;
    color: rgb(0, 0, 0);
    margin: 1px 3px 1px 3px
}

#foraDoEscopo button:hover {
    border: 2px solid rgb(255, 0, 0);
    background-color: red;

}

</style>