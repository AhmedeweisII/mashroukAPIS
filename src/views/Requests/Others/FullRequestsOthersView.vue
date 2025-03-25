<!-- eslint-disable vuejs-accessibility/click-events-have-key-events -->
<!-- eslint-disable max-len -->
<!-- eslint-disable vuejs-accessibility/anchor-has-content -->
<!-- eslint-disable vuejs-accessibility/alt-text -->
<template>
  <section class="delete-head  m-t-20">
    <div class="container">
      <div>
        <Button @click="goBack" class="b-t"><img class="icone-resize" src="../../../assets/imgs/right-arrow.png" alt=""></Button>
      </div>

      <div class="m-r-20 justfy-c">
        <h3 class="" style="font-size:19px; color: #396FB5;"> طلب رقم {{ shortenId(mockRealEstate.id) }}</h3>
      </div>
      <button id="shareButton" class="" style="background-color: transparent;">
        <img src="../../../assets/imgs/shareing.png" alt="Share" style="width: 30px">
      </button>
    </div>
  </section>
  <section class="slider-sec">
    <div class="container">
      <div class="slider-container">
        <div class="slider">
          <div class="slide"><img src="../../../assets/imgs/1.png" alt="Image 1" class="slider-img"></div>
          <div class="slide"><img src="../../../assets/imgs/2.png" alt="Image 2" class="slider-img"></div>
          <div class="slide"><img src="../../../assets/imgs/3.png" alt="Image 3" class="slider-img"></div>
          <div class="slide"><img src="../../../assets/imgs/4.png" alt="Image 4" class="slider-img"></div>
          <div class="slide"><img src="../../../assets/imgs/5.png" alt="Image 5" class="slider-img"></div>
        </div>
        <button class="prev"><img src="">❯</button>
        <button class="next"><img src="">❮</button>
        <div class="slider-nav"></div>
      </div>
    </div>
  </section>
  <section class="Request-info">
    <div class="container">

      <div class="info-header">
        <h2 class="info-head">{{  getproperty_typeById(mockRealEstate.property_type) }}</h2>  <!--   -->
        <!-- <div class="filed-data">
                    <img src="../assets/imgs/to-do-list.png" class="icone-resize">
                    <h2 class="data-lable"> &nbsp;رقم الطلب &nbsp;:&nbsp;</h2>
                    <h3 class="data-value">10009&nbsp;</h3>
                    <p class="Request-num min-Request-num">(استثمار)</p>
                </div> -->
        <div class="Request-box">
          <img src="../../../assets/imgs/to-do-list.png" class="icone-resize" style="margin-left: 5px;">
          <p class="Request-label">رقم الطلب : {{ shortenId(mockRealEstate.id) }} </p>
          <!-- <p class="Request-num">{{ partnerId }}</p> -->
        </div>

      </div>

      <div class="owner-name-header">
        <div class="owner-name-head">
          <div class="owner-name"> {{  owner ? owner : 'بدون اسم' }} </div>
          <!-- <div class="owner-prop"> ( وسيط عقاري )</div> -->
        </div>
        <div class="stars">
          <img src="../../../assets/imgs/full-star.png" class="star-photo">
          <img src="../../../assets/imgs/full-star.png" class="star-photo">
          <img src="../../../assets/imgs/full-star.png" class="star-photo">
          <img src="../../../assets/imgs/full-star.png" class="star-photo">
          <img src="../../../assets/imgs/empaty-star.png" class="star-photo">
        </div>
      </div>

      <div class="client-num">
        <div class="client-num min-req-client-num">
          <template v-for="(item, i) in Array.from({ length: entered + 1 })" :key="i">
            <img v-if="i <= entered" src="../../../assets/imgs/AvatarPurbile.svg" class="client-image">
          </template>
          <template v-for="(item, i) in Array.from({ length: mockRealEstate.partners_count - entered - 1})" :key="i">
            <img src="../../../assets/imgs/Avatar.svg" class="client-image">
          </template>
        </div>
      </div>
    </div>
  </section>
  <section class="details-sections">
    <div class="container">
      <header class="data-head">
        <div class="link" @click="toggleVar" :class="{ 'link-active': RenderAd() }">تفاصيل الشراكة</div>
        <div class="link" @click="toggleVar" :class="{ 'link-active': RenderDetails() }">تفاصيل العقار</div>
      </header>

      <div class="data-catcher">
        <div class="aqar-details" v-if="RenderDetails()">

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/location.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">المدينة</h2>
            </div>
            <h3 class="data-value">{{ getCityNameById(mockRealEstate.city_id) || '' }}</h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/location.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">الحي</h2>
            </div>
            <h3 class="data-value">{{ mockRealEstate.partnerNeighborhoods }}</h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/house.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">النوع</h2>
            </div>
            <h3 class="data-value">{{ getproperty_typeById(mockRealEstate.property_type) }}</h3>
            <!-- mockRealEstate.property_type -->
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/work-tools.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">عرض الشارع</h2>
            </div>
            <h3 class="data-value">{{ mockRealEstate.street_width }} م</h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/area.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">المساحة</h2>
            </div>
            <h3 class="data-value">{{ mockRealEstate.property_area }} متر مربع</h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/cubeI.png" class="icone-resize marg-l-5">
              <h2 class="data-lable"> الواجهة</h2>
            </div>
            <h3 class="data-value">{{ mockRealEstate.directions }}</h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/sign.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">رقم المخطط</h2>
            </div>
            <h3 class="data-value">{{ mockRealEstate.plan_number }}</h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/tag.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">رقم القطعة</h2>
            </div>
            <h3 class="data-value">{{ mockRealEstate.property_number }}</h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/hourglass.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">عمر العقار</h2>
            </div>
            <h3 class="data-value">{{ mockRealEstate.property_age }} سنة</h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/hallway.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">عدد الوحدات</h2>
            </div>
            <h3 class="data-value"> {{ units_number }} وحدات</h3>
          </div>
          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/building.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">عدد الادوار</h2>
            </div>
            <h3 class="data-value"> {{ levels_number }} دور</h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/apartment.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">عدد الشقق</h2>
            </div>
            <h3 class="data-value"> {{apartments_number}} شقق</h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/store.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">عدد المحلات</h2>
            </div>
            <h3 class="data-value"> {{ shop_number }} محلات </h3>
          </div>

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/workspace.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">عدد المكاتب</h2>
            </div>
            <h3 class="data-value"> {{ office_number }} مكاتب</h3>
          </div>

          <div class="data-filed">
            <h2 class="data-lable">الموقع علي الخريطة</h2>
            <img src="../../../assets/imgs/1000x500.png" class="map-photo">
          </div>

        </div>
        <div class="ad-details" v-if="RenderAd()">
          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/calendar.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">تاريخ إضافة الطلب</h2>
            </div>
            <h3 class="data-value">{{  convertTimestampToFormalDateTime(mockRealEstate.dateCreated) }}</h3>
          </div>
          <!--
                <div class="data-filed">
                    <h2 class="data-lable">الغرض</h2>
                    <h3 class="data-value">سكني</h3>
                </div> -->

          <div class="data-filed">
            <div class="filed-flex">
              <img src="../../../assets/imgs/money.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">مبلغ الشراكة </h2>
              <div class="talk"> ( لكل شريك)</div>
            </div>
            <div class="data-value">
              <h3 class="value">{{ mockRealEstate.investment_cost }}  ريال</h3>
              <div class="talk" v-if="mockRealEstate.negotiable === 1">قابل للتفاوض</div>
            </div>
          </div>

          <div class="general-chat-handle">
            <div class="filed-flex">
              <img src="../../../assets/imgs/team.png" class="icone-resize marg-l-5">
              <h2 class="data-lable">عدد الشركاء الحاليين</h2>
              <div class="talk">{{entered + 1}}/{{mockRealEstate.partners_count}}</div>
            </div>
            <!-- <a href="payment.html" class="nav-link" style="text-align: center;">
                        <img src="../assets/imgs/chat-box.png" class="" width="50px">
                        <h3 class="bottom-nav-word" style="color: #396FB5;"> فتح الدردشة</h3>
                    </a> -->
          </div>
          <!--  -->

          <!-- 0 time line -->
          <section class="bullets  m-t-20">
            <div class="container">
              <!-- 0 head-box -->
              <div class="head-box">
                <div class="head-box-flex">
                  <div class="circle circle-active ">
                    <p>1</p>
                  </div>
                  <div class="head-titlte ">
                    انتظار الموافقة علي الشركاء
                  </div>
                </div>
                <routerLink :to="{ name: 'AcceptListOthers', params: { id: `${this.commercialsId}`} }" class="small-btn head-box-flex">
                  قائمة الانتظار <p>&nbsp;({{ waiters }})</p>
                </routerLink>
              </div>
              <!-- 1 head-box -->
              <div class="line"></div>

              <!-- 0 head-box -->
              <div class="head-box">
                <div class="head-box-flex">
                  <div class="circle circle-active ">
                    <p>2</p>
                  </div>
                  <div class="head-titlte ">
                    دفع رسوم الخدمة
                  </div>
                </div>
                <routerLink to="/PaymentGetWays" class="small-btn head-box-flex">ادفع</routerLink>
                <button class="small-btn accept-btn" @click="enterRequest()">ادفع له</button>
              </div>
              <!-- 1 head-box -->
              <div class="line"></div>

              <!-- 0 head-box -->
              <div class="head-box">
                <div class="head-box-flex">
                  <div class="circle circle-active ">
                    <p>3</p>
                  </div>
                  <div class="head-titlte ">
                    انتظار دفع الشركاء
                  </div>
                </div>
                <routerLink :to="{ name: 'PaymentListOthers', params: { id: `${this.commercialsId}`} }" class="small-btn head-box-flex">
                  تفاصيل الدفع<p>&nbsp;({{ entered }}/{{ payners + entered }})</p>
                </routerLink>
              </div>
              <!-- 1 head-box -->
              <div class="line "></div>
              <!-- 0 head-box -->
              <div class="head-box ">
                <div class="head-box-flex">
                  <div class="circle circle-active ">
                    <p class="">4</p>
                  </div>
                  <div class="head-titlte ">
                    تم الانضمام
                  </div>
                </div>
                <router-link to="/Converztions" class="small-btn head-box-flex ">
                  الدخول
                  للمحادثة
                </router-link>

              </div>
              <!-- 1 head-box -->

            </div>
          </section>

          <!-- 1 time line -->

        </div>

      </div>

    </div>
  </section>

  <!-- <div class="container">
<div style="display: flex; justify-content: space-between; padding:30px 0;">
    <a class="small-btn" href="succes.html">حفظ</a>
    <a class="small-btn" href="land.html"style="background-color:transparent; color:var(--main-color); border:none;">رجوع</a>
</div>
</div> -->

<section class="actions reflex" style="margin-bottom: 10px;">
  <div class="container">
      <div class="another-acrions">
        <router-link :to="{ name: 'AddOffer', params: { id: `${this.commercialsId}/${this.mockRealEstate.partners_count}`}}" style="width: max-content; min-width: 100px;" class="mashrouk-btn main-req-button">
          <h4>أنضم كشريك</h4>
        </router-link>
          <a href="" class=" main-req-button m-r"> <!-- .expline  -->
              <img src="../../../assets/imgs/heart.png" class="main-req-button-img" >
            </a>
      </div>
  </div>
</section>

</template>
<script>
import { BASE_URL } from '@/api-config';
import axios from 'axios';
import { createToaster } from '@meforma/vue-toaster';

export default {
  name: 'FullRequestsOthers',
  data() {
    return {
      Ad: true,
      commercialsId: null,
      owner: {},
      cities: [],
      office_number: 0,
      apartments_number: 0,
      levels_number: 0,
      shop_number: 0,
      units_number: 0,
      description: '',
      requests: [],
      waiters: 0,
      payners: 0,
      entered: 0,
      targetPayRequests: [],
      Iduser: '',
      extractedId: null,
      user_name: '',
      enterRequestStatusCode: null,
      mockRealEstate: [
  {
    id: '1',
    property_type: 2, // Villa
    owner: { name: 'علي محمد', id: 'user-123' },
    dateCreated: new Date('2023-05-15').toISOString(),
    city_id: 1,
    partnerNeighborhoods: 'حي النخيل',
    partners_count: 4,
    investment_cost: 450000,
    purpose: 0, // Investment
    partner_type: 'استثمار',
    description: '400,2,5,3,8', // units,office,apartments,levels,shop
    street_width: 20,
    property_area: 400,
    directions: 'شمال',
    plan_number: '12345',
    property_number: '678',
    property_age: 5,
    negotiable: 1,
    images: [
      '1.png',
      '2.png',
      '3.png'
    ]
  },
  {
    id: '2',
    property_type: 1, // Land
    owner: { name: 'سالم عبدالله', id: 'user-456' },
    dateCreated: new Date('2023-06-20').toISOString(),
    city_id: 2,
    partnerNeighborhoods: 'حي الربيع',
    partners_count: 5,
    investment_cost: 320000,
    purpose: 1, // Ownership
    partner_type: 'تملك',
    description: '600,0,0,0,0',
    street_width: 15,
    property_area: 600,
    directions: 'شرق',
    plan_number: '54321',
    property_number: '901',
    property_age: 0,
    negotiable: 0,
    images: [
      '4.png',
      '5.png'
    ]
  },
  {
    id: '3',
    property_type: 4, // Condominium
    owner: { name: 'مريم خالد', id: 'user-789' },
    dateCreated: new Date('2023-07-10').toISOString(),
    city_id: 1,
    partnerNeighborhoods: 'حي الصحافة',
    partners_count: 3,
    investment_cost: 280000,
    purpose: 0,
    partner_type: 'استثمار',
    description: '6,2,6,4,0',
    street_width: 18,
    property_area: 800,
    directions: 'غرب',
    plan_number: '67890',
    property_number: '234',
    property_age: 3,
    negotiable: 1,
    images: [
      '6.png',
      '7.png',
      '8.png'
    ]
  },
  {
    id: '4',
    property_type: 14, // Commercial
    owner: { name: 'شركة الأفق العقارية', id: 'user-101' },
    dateCreated: new Date('2023-08-05').toISOString(),
    city_id: 3,
    partnerNeighborhoods: 'حي المركز',
    partners_count: 6,
    investment_cost: 750000,
    purpose: 0,
    partner_type: 'استثمار',
    description: '10,10,0,2,10',
    street_width: 25,
    property_area: 1200,
    directions: 'جنوب',
    plan_number: '13579',
    property_number: '567',
    property_age: 2,
    negotiable: 1,
    images: [
      '9.png',
      '10.png'
    ]
  },
  {
    id: '5',
    property_type: 17, // Villa with internal stairs
    owner: { name: 'فهد الرشيد', id: 'user-202' },
    dateCreated: new Date('2023-09-12').toISOString(),
    city_id: 1,
    partnerNeighborhoods: 'حي الورود',
    partners_count: 2,
    investment_cost: 380000,
    purpose: 1,
    partner_type: 'تملك',
    description: '350,1,1,2,0',
    street_width: 22,
    property_area: 350,
    directions: 'شمال شرق',
    plan_number: '24680',
    property_number: '890',
    property_age: 4,
    negotiable: 0,
    images: [
      '11.png',
      '12.png',
      '13.png'
    ]
  }
],
    };
  },
  props: {
    id: {
      type: String,
      required: true,
    },
  },
  mounted() {
    this.getuserID();
    this.getRequestsByPost();
    this.fetchConversations();
  },
  created() {
    const [id, ownerString] = this.$route.params.id.split('/');
    this.commercialsId = id;
    this.owner = ownerString;

    this.fetchCommercialData();
    this.fetchCities();
    this.getRequestsByPost();
    // this.addUserToConversation();
  },
  watch: {
    enterRequestStatusCode(newStatusCode) {
      // Watch for changes in enterRequestStatusCode
      if (newStatusCode === 200) {
        // If enterRequestStatusCode becomes 200, proceed with adding the user to the conversation
        this.addUserToConversation();
      } else {
        console.warn('Enter request status code is not 200. User addition to conversation is not triggered.');
      }
    },
  },
  computed: {
    activeClass() {
      return {
        'link-active': this.RenderAd(),
      };
    },
    payingRequests() {
      return this.requests.filter((request) => request.status === 'paying');
    },
    waitingRequests() {
      return this.requests.filter((request) => request.status === 'waiting');
    },
    enteredRequests() {
      // Filter requests with status "waiting"
      return this.requests.filter((request) => request.status === 'entered');
    },
  },
  methods: {
    async getRequestsByPost() {
      try {
        const response = await axios.get(`http://localhost:3000/api/requests-by-post/${this.commercialsId}`);
        this.requests = response.data.requestsByPost;

        // Normalize Iduser by removing double quotes
        const normalizedIduser = this.Iduser.replace(/"/g, '');

        // Filter requests based on Iduser
        this.targetPayRequests = response.data.requestsByPost.filter((request) => {
          const normalizedUserId = request.userid.replace(/"/g, '');
          return normalizedUserId === normalizedIduser;
        });

        // Extract requestid for the filtered requests
        const extractedRequestIds = this.targetPayRequests.map((request) => request.requestid);

        console.log('All requests:', this.requests);
        console.log('Filtered requests:', this.targetPayRequests);
        console.log('Extracted request ids:', extractedRequestIds);

        this.waiters = this.waitingRequests.length;
        this.payners = this.payingRequests.length;
        this.entered = this.enteredRequests.length;
      } catch (error) {
        // Handle errors
        console.error(error);
      }
    },
    async getuserID() {
      const rawIduser = localStorage.getItem('userId');
      const username = localStorage.getItem('user');
      this.Iduser = rawIduser;
      this.user_name = username;
      console.log('Iduser:', this.Iduser);
    },
    async enterRequest() {
      console.log('Entering enterRequest function');
      const toaster = createToaster();

      // Make sure 'targetPayRequests' is not empty
      if (this.targetPayRequests.length > 0) {
        // Assuming you want to work with the first element of 'targetPayRequests'
        const { requestid } = this.targetPayRequests[0];

        // Make sure 'requestid' is a valid value
        if (requestid) {
          try {
            // Call the API to update the request to 'entered'
            const response = await axios.post(`http://localhost:3000/api/enter-request/${requestid}`);

            // Save the status code in a data property
            this.enterRequestStatusCode = response.status;

            // Check if the response code indicates success (200 or 201)
            if (response.status === 200) {
              // Show a success toast
              const toast = toaster();
              toast.success('تم تحديث العرض للحالة "entered"');
              this.$router.push('/AcceptList');
            }
          } catch (error) {
            // Handle errors
            console.error(error);
          }
        } else {
          console.error('Invalid requestId');
        }
      } else {
        console.error('targetPayRequests is empty');
      }
    },

    async addUserToConversation() {
      try {
        // Make an API request to add user to conversation
        await axios.post('http://localhost:3000/api/add-user-to-conversation', {
          conversationId: this.extractedId,
          userId: this.Iduser,
          userName: this.user_name,
        });

        // Clear form fields after successfully adding user to conversation
        this.conversation_id = '';
        this.user_id = '';
        this.user_name = '';

        // Optionally, you can emit an event to notify the parent component about the update
        this.$emit('userAddedToConversation');

        // Optionally, you can also redirect to another route or display a success message
      } catch (error) {
        console.error('Error adding user to conversation:', error.response || error.message || error);
        // Handle error and display an error message if needed
      }
    },
    async fetchConversations() {
      try {
        const response = await fetch(`http://localhost:3000/api/conversations-by-post/${this.commercialsId}`);
        const data = await response.json();

        // Assuming the API response has a "data" field
        this.responseData = data.data;

        // Extracting ID from the first object in the "data" array (adjust as needed)
        this.extractedId = this.responseData.length > 0 ? this.responseData[0].id : null;
      } catch (error) {
        console.error('Error fetching conversations:', error);
        this.responseData = null; // Reset responseData in case of an error
        this.extractedId = null; // Reset extractedId in case of an error
      }
    },
    goBack() {
      // Use Vue Router to go back
      this.$router.go(-1);
    },
    toggleVar() {
      this.Ad = !this.Ad;
    },
    RenderAd() {
      return this.Ad;
    },
    RenderDetails() {
      return !this.Ad;
    },
    async fetchCommercialData() {
  try {
    const response = await axios.get(
      `${BASE_URL}/POST/GetPOST?IDPOST=${this.commercialsId}`,
    );

    // Update with real data
    this.mockRealEstate = response.data;
    this.processDescription(response.data.description);
    this.useMockData = false;
  } catch (error) {
    console.error('Error fetching commercial data, using mock data:', error);
    this.useMockData = true;

    // Find mock data by ID or use first item
    const mockItem = this.mockRealEstate.find((item) => item.id === this.commercialsId)
                    || this.mockRealEstate[0];

    this.mockRealEstate = mockItem;
    this.processDescription(mockItem.description);
  }
},

processDescription(description) {
  if (description) {
    const [units, office, apartments, levels, shop] = description.split(',');
    this.units_number = units || 0;
    this.office_number = office || 0;
    this.apartments_number = apartments || 0;
    this.levels_number = levels || 0;
    this.shop_number = shop || 0;
  }
},
    async fetchCities() {
      const headers = {
        'Content-Type': 'application/json',
        Authorization: `Bearer ${this.token}`,
      };

      try {
        const response = await axios.get(`${BASE_URL}/Home/GetCities`, { headers });
        this.cities = response.data;
      } catch (error) {
        console.error('Error fetching cities:', error);
      }
    },
    shortenId(id) {
      // Check if id is defined and a string
      if (id && typeof id === 'string') {
        const parts = id.split('-');
        return parts[0];
      }
      return '';
    },
    getproperty_typeById(propertyTypeId) {
      switch (propertyTypeId) {
        case 1:
          return 'ارض';
        case 2:
          return 'فيلا';
        case 3:
          return 'عمارة';
        case 4:
          return 'عمارة (شقق سكنية)';
        case 5:
          return 'عمارة شقق مفروشة';
        case 6:
          return 'عمارة محلات و شقق سكنية';
        case 7:
          return 'عمارة محلات و شقق مفروشة';
        case 8:
          return 'عمارة محلات';
        case 9:
          return 'عمارة محلات ومكاتب';
        case 10:
          return 'عمارة مكاتب';
        case 11:
          return 'بلازا';
        case 12:
          return 'سكني  ';
        case 13:
          return 'سكني تجاري';
        case 14:
          return 'تجاري';
        case 15:
          return 'زراعي';
        case 16:
          return 'صناعي';
        case 17:
          return 'فيلا درج داخلي وشقة';
        case 18:
          return 'فيلا دورين';
        case 20:
          return 'فيلا دورين وملحق';
        default:
          return 'عقار غير معروف';
      }
    },
    getCityNameById(cityId) {
    // First try to get city from API data
    if (this.cities && this.cities.length > 0) {
      const city = this.cities.find((c) => c.city_id === cityId);
      if (city) return city.name_ar;
    }
    // Fallback to static Saudi cities data
    const saudiCities = {
      1: 'الرياض',
      2: 'جدة',
      3: 'مكة المكرمة',
      4: 'المدينة المنورة',
      5: 'الدمام',
      6: 'الخبر',
      7: 'الطائف',
      8: 'تبوك',
      9: 'بريدة',
      10: 'خميس مشيط',
      11: 'حائل',
      12: 'الجبيل',
      13: 'أبها',
      14: 'نجران',
      15: 'ينبع',
      16: 'القنفذة',
      17: 'الاحساء',
      18: 'عرعر',
      19: 'سكاكا'
    };
    return saudiCities[cityId] || 'غير معروف';
  },
    convertTimestampToFormalDateTime(timestamp) {
      const dateObj = new Date(timestamp);

      const day = dateObj.getDate().toString().padStart(2, '0');
      const month = (dateObj.getMonth() + 1).toString().padStart(2, '0'); // Months are zero-based
      const year = dateObj.getFullYear();

      return `${day}/${month}/${year}`;
    },
  },
};
</script>
