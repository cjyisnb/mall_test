<template>
  <div class="wrapper" ref="aaaa">
    <ul class="content">
      <li>aaa1</li>
      <li>aaa2</li>
      <li>aaa3</li>
      <li>aaa4</li>
      <li>aaa5</li>
      <li>aaa6</li>
      <li>aaa7</li>
      <li>aaa8</li>
      <li>aaa9</li>
      <li>aaa10</li>
      <li>aaa11</li>
      <li>aaa12</li>
      <li>aaa13</li>
      <li>aaa14</li>
      <li>aaa15</li>
      <li>aaa16</li>
      <li>aaa17</li>
      <li>aaa18</li>
      <li>aaa19</li>
      <li>aaa20</li>
      <li>aaa21</li>
      <li>aaa22</li>
      <li>aaa23</li>
      <li>aaa24</li>
      <li>aaa25</li>
      <li>aaa26</li>
      <li>aaa27</li>
      <li>aaa28</li>
      <li>aaa29</li>
      <li>aaa30</li>
      <li>aaa31</li>
      <li>aaa32</li>
      <li>aaa33</li>
      <li>aaa34</li>
      <li>aaa35</li>
      <li>aaa36</li>
      <li>aaa37</li>
      <li>aaa38</li>
      <li>aaa39</li>
      <li>aaa40</li>
      <li>aaa1</li>
      <li>aaa2</li>
      <li>aaa3</li>
      <li>aaa4</li>
      <li>aaa5</li>
      <li>aaa6</li>
      <li>aaa7</li>
      <li>aaa8</li>
      <li>aaa9</li>
      <li>aaa10</li>
      <li>aaa11</li>
      <li>aaa12</li>
      <li>aaa13</li>
      <li>aaa14</li>
      <li>aaa15</li>
      <li>aaa16</li>
      <li>aaa17</li>
      <li>aaa18</li>
      <li>aaa19</li>
      <li>aaa20</li>
      <li>aaa21</li>
      <li>aaa22</li>
      <li>aaa23</li>
      <li>aaa24</li>
      <li>aaa25</li>
      <li>aaa26</li>
      <li>aaa27</li>
      <li>aaa28</li>
      <li>aaa29</li>
      <li>aaa30</li>
      <li>aaa31</li>
      <li>aaa32</li>
      <li>aaa33</li>
      <li>aaa34</li>
      <li>aaa35</li>
      <li>aaa36</li>
      <li>aaa37</li>
      <li>aaa38</li>
      <li>aaa39</li>
      <li>aaa40</li>
      <li>aaa1</li>
      <li>aaa2</li>
      <li>aaa3</li>
      <li>aaa4</li>
      <li>aaa5</li>
      <li>aaa6</li>
      <li>aaa7</li>
      <li>aaa8</li>
      <li>aaa9</li>
      <li>aaa10</li>
      <li>aaa11</li>
      <li>aaa12</li>
      <li>aaa13</li>
      <li>aaa14</li>
      <li>aaa15</li>
      <li>aaa16</li>
      <li>aaa17</li>
      <li>aaa18</li>
      <li>aaa19</li>
      <li>aaa20</li>
      <li>aaa21</li>
      <li>aaa22</li>
      <li>aaa23</li>
      <li>aaa24</li>
      <li>aaa25</li>
      <li>aaa26</li>
      <li>aaa27</li>
      <li>aaa28</li>
      <li>aaa29</li>
      <li>aaa30</li>
      <li>aaa31</li>
      <li>aaa32</li>
      <li>aaa33</li>
      <li>aaa34</li>
      <li>aaa35</li>
      <li>aaa36</li>
      <li>aaa37</li>
      <li>aaa38</li>
      <li>aaa39</li>
      <li>aaa40</li>
    </ul>
  </div>

</template>

<script>
  import BScroll from 'better-scroll'

  export default {
    name: "Category",
    data() {
      return {
        scroll: null
      }
    },
    mounted() {
      this.scroll = new BScroll(this.$refs.aaaa, {
        // probeType: 3,
        // pullUpLoad: true
      })

      this.scroll.on('scroll', (position) => {
        console.log(position);
      })

      this.scroll.on('pullingUp', () => {
        console.log('上啦加载更多');
      })
    }
  }
</script>

<style scoped>
  .wrapper{
    height: 150px;
    background-color: red;
    overflow: hidden;
  }
</style>
