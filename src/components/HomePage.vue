<template>
    <div id="homePage">
        <table id="bordMagic">
            <tr>
                <td> ID </td>
                <td> Nome </td>
                <td> Idade </td>
                <td> Cep </td>
                <td> Idade </td>
                <td> Estado </td>
                <td> Editar Item</td>
                <td> Deletar Item</td>
            </tr>
            
            <tr v-for="items in myListArray" :key="items.key">
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
            <button type="button" @click="addNewItem"> Add New Item</button>
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
    border: 1px solid black;

}

#bordMagic td {
    border: 1px solid black;


}

#bordMagic tr {
    border: 1px solid black;
}

</style>