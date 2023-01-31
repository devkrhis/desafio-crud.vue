<template>
    <div id="homePage">
        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
        <link href="https://fonts.googleapis.com/css2?family=Kanit&display=swap" rel="stylesheet">
        <h1> Listar Usuários </h1>
        <div id="ControlTable">
            <table id="ControlIntegerTable">
                <tr id="TableHeader"> 
                    <td> ID </td>
                    <td> Nome </td>
                    <td> Idade </td>
                    <td> Cep </td>
                    <td> Cidade </td>
                    <td> Estado </td>
                    <td> Editar Item</td>
                    <td> Deletar Item</td>
                </tr>
                
                <tr id="itemsTable" v-for="items in myListArray" :key="items.key">
                    <td> {{ items.id }}</td>
                    <td> {{ items.nome }}</td>
                    <td> {{ items.idade }}</td>
                    <td> {{ items.Local.cep }}</td>
                    <td> {{ items.Local.cidade }}</td>
                    <td> {{ items.Local.estado }}</td>
                    <td> <button type="button" @click="editObject(items.id)"> Edit Object</button> </td>
                    <td> <button type="button" @click="deletAll(items.id)"> Delet Object</button> </td>
                </tr>
                <div id="GlobalUpdateButtons">
                    <button type="button" @click="addNewItem"> Add New Item</button>
                    <button type="button" @click="DoubleAge"> Multiplier Age</button>
                </div>
            </table>
        </div>

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

#homePage {
    align-items: center;
    font-family: 'Kanit', sans-serif;

}

h1 {
    text-align: center;
}

td{ 
    padding: 20px 50px 20px 50px;
   
}

#ControlTable {
    display: flex;
    justify-content: center;
    background-color: rgba(5, 0, 0, 0.192);
    margin-right: 100px;
    margin-left: 100px;
    

}

#ControlIntegerTable {
    border-collapse: collapse;
    background-color: white;

}


#TableHeader {
   background-color: rgb(82, 82, 240); 
   font-size: large;
   
}

#itemsTable {
    background-color: white;
    border: 1px solid black;
    
}

#itemsTable button {
    margin: 5px 7px;
    padding: 10px;
    font-size: medium;
    background-color: rgb(3, 187, 3);
    box-shadow:0 5px 0 #006000;
    border: 1px solid
    
}

#itemsTable button:hover {
    background:#006000;
    box-shadow:0 5px 0 #003f00;
    
}

#itemsTable button:active {
    background-color: rgb(255, 230, 0);
    position: relative;
    top: 5px;
    box-shadow: none;
    
}

#GlobalUpdateButtons {
    display: flex;
    justify-content: center;
}

#GlobalUpdateButtons button {
    font-size: medium;
    border: 1px solid;
    margin-top: 2px;
    margin-left: 1px;
    background-color: rgb(3, 187, 3);
    box-shadow:0 5px 0 #006000;
    border: 1px solid;
    padding: 0px 25px 0px 25px;
}

#GlobalUpdateButtons button:hover {
    background:#006000;
    box-shadow:0 5px 0 #003f00;
    
}

#GlobalUpdateButtons button:active {
    background-color: rgb(255, 230, 0);
    position: relative;
    top: 5px;
    box-shadow: none;
    
}


</style>

topo direita inferior esquerda