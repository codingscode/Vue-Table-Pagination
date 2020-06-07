<template>
      <section class="table">
          <table>
              <thead>
                 <tr>
                     <th v-for="(object, index) in settings" :key="index">
                          {{object.title}}
                     </th>
                 </tr>
              </thead>
              <tbody>
                  <tr v-for="(line, i) in theData" :key="i">
                      <td v-for="(object, index) in settings" :key="index">
                          <span v-if="object.type === 'text'">{{line[object.key]}}</span>
                          <span v-if="object.type === 'date'">{{new Date(line[object.key]).toLocaleDateString()}}</span>
                          <figure v-if="object.type === 'image'">
                              <img :src="line[object.key]" height="80px" width="100px">
                          </figure>
                      </td>
                  </tr>
              </tbody>
          </table>
      </section>
</template>

<script>
export default {
   props: ['theData','settings']
}
</script>

<style lang="scss">
.table {
    border: 1px solid #999;
    border-radius: 9px;
    color: #333;
    overflow: auto;
    width: 1000px;
    margin: 50px;
    background-color: white;

    figure {
        margin-block-start: 0;
        margin-block-end: 0;
        margin-inline-start: 0;
        margin-inline-end: 0;

        img {
            border: 1px solid #bbb;
            border-radius: 50%;
            overflow: hidden;
        }
    }

    table {
        border-collapse: collapse;
        width: 100%;

        th {
            position: sticky;
            top: 0;
            background: #0f2862;
            padding: 10px 5px;
            text-align: left;
            border-bottom: 1px solid grey;
            color: gold;
            text-align: center;
        }
        
        td {
            padding: 5px 5px;
            text-align: left;
            color: darkgreen;
            font-weight: 900;
            font-family:Arial, Helvetica, sans-serif;
            text-align: center;
        }
    }
}

</style>