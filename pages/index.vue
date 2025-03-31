<script setup>
const currentRole = ref('worker') // Default role is worker
const showRoleSwitcher = ref(false)

// Handle scroll event
onMounted(() => {
  window.addEventListener('scroll', () => {
    showRoleSwitcher.value = window.scrollY > 95
  })
})

onUnmounted(() => {
  window.removeEventListener('scroll', () => {
    showRoleSwitcher.value = window.scrollY > 95
  })
})

//???
const advantages = computed(() => {
  if (currentRole.value === 'worker') {
    return [
      {
        icon: '🚀',
        title: 'Быстрый старт',
        description: 'Зарегистрируйтесь и начните выполнять заказы уже сейчас!'
      },
      {
        icon: '💎',
        title: 'Честные условия',
        description: 'Четко указанные комиссии, без скрытых списаний'
      },
      {
        icon: '🛡️',
        title: 'Гарантии оплаты',
        description: 'Безопасная сделка - оплата поступит сразу после выполнения работы'
      }
    ]
  } else {
    return [
      {
        icon: '🎯',
        title: 'Проверенные исполнители',
        description: 'Только квалифицированные специалисты с подтвержденными навыками'
      },
      {
        icon: '⚡',
        title: 'Быстрый поиск',
        description: 'Находите подходящих исполнителей за считанные минуты'
      },
      {
        icon: '🔒',
        title: 'Безопасность',
        description: 'Гарантия качества выполнения работы или возврат средств'
      }
    ]
  }
})

const reviews = computed(() => {
  if (currentRole.value === 'worker') {
    return [
      {
        id: 1,
        name: 'Иван Смирнов',
        position: 'Репетитор по математике',
        rating: 5,
        text: 'Удобная платформа для поиска заказов. Работаю здесь уже год и очень доволен!'
      },
      {
        id: 2,
        name: 'Мария Раздорская',
        position: 'Дизайнер',
        rating: 5,
        text: 'Отличная площадка для профессионального роста. Много интересных проектов.'
      },
      {
        id: 3,
        name: 'Алексей Петров',
        position: 'None',
        rating: 1,
        text: 'Мне не понравилось.'
      }
    ]
  } else {
    return [
      {
        id: 1,
        name: 'Анна Петрова',
        position: 'CEO, TechStart',
        rating: 5,
        text: 'Отличная платформа для поиска специалистов. Нашли разработчика за 2 дня!'
      },
      {
        id: 2,
        name: 'Сергей Козлов',
        position: 'Предприниматель',
        rating: 5,
        text: 'Быстро нашел дизайнера для своего проекта. Качество работы превзошло ожидания.'
      },
      {
        id: 3,
        name: 'Елена Соколова',
        position: 'Менеджер проектов',
        rating: 5,
        text: 'Удобный сервис для поиска фрилансеров. Все прозрачно и надежно.'
      }
    ]
  }
})

const projects = computed(() => {
  if (currentRole.value === 'worker') {
    return [
      {
        id: 1,
        title: 'Уборка снега',
        description: 'Расчистить от снега выезд из парковки',
        payment: '3 000 ₽'
      },
      {
        id: 2,
        title: 'Мытье тротуара',
        description: 'Помыть тротуар от грязи, средства выдадим',
        payment: '2 500 ₽'
      },
      {
        id: 3,
        title: 'Полив растений',
        description: 'Требуется поухаживать за садом в течение 4 часов',
        payment: '1 634 ₽'
      }
    ]
  }
})
</script>

<template>
  <div class="min-h-screen bg-gradient-to-b from-gray-50 to-white w-full">
    <!-- Role Switcher -->
    <div class="fixed top-4 right-4 z-50 bg-white rounded-full shadow-lg p-1 transition-all duration-300 w-30" :class="[
      showRoleSwitcher ? 'opacity-100 translate-y-0' : 'opacity-0 -translate-y-full'
    ]">
      <div class="flex gap-1">
        <button @click="currentRole = 'worker'" :class="[
          'px-4 py-2 rounded-full transition-all duration-300',
          currentRole === 'worker'
            ? 'bg-primary text-white'
            : 'hover:bg-gray-100'
        ]">
          Исполнитель
        </button>
        <button @click="currentRole = 'employer'" :class="[
          'px-4 py-2 rounded-full transition-all duration-300',
          currentRole === 'employer'
            ? 'bg-primary text-white'
            : 'hover:bg-gray-100'
        ]">
          Заказчик
        </button>
      </div>
    </div>

    <!-- Hero Section with animated background -->
    <section class="relative bg-gradient-to-r from-indigo-600 to-indigo-800 text-white py-16 md:py-32 overflow-hidden">
      <div class="absolute inset-0 overflow-hidden">
        <div
          class="absolute inset-0 bg-[url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAiIGhlaWdodD0iNjAiIHZpZXdCb3g9IjAgMCA2MCA2MCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48ZyBmaWxsPSJub25lIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiPjxwYXRoIGQ9Ik0zNiAxOGMzLjMxIDAgNiAyLjY5IDYgNnMtMi42OSA2LTYgNi02LTIuNjktNi02IDIuNjktNiA2LTZ6IiBzdHJva2U9InJnYmEoMjU1LDI1NSwyNTUsMC4xKSIgc3Ryb2tlLXdpZHRoPSIyIi8+PC9nPjwvc3ZnPg==')] opacity-10 animate-[spin_60s_linear_infinite]">
        </div>
      </div>
      <div class="relative">
        <v-row no-gutters>
          <v-col cols="12">
            <div class="py-16">
              <v-row align="center" justify="center">
                <v-col cols="12" md="8" class="text-center">
                  <h1 class="text-white text-h1 font-weight-black mb-6" style="font-family: 'Montserrat', sans-serif;">
                    {{ currentRole === 'worker' ? 'Найдите прибыльную подработку' : 'Найдите людей для вашей задачи' }}
                  </h1>
                  <p class="text-white text-h5 font-weight-regular mb-8">
                    {{ currentRole === 'worker'
                      ? 'Деньги 200 метров от вас'
                      : 'Считайте что работа уже сделана' }}
                  </p>
                  <NuxtLink to="/sign">
                    <v-btn size="x-large" color="white" class="text-primary font-weight-bold px-8 text-body-1">
                      {{ currentRole === 'worker' ? 'Найти работу' : 'Найти работника' }}
                    </v-btn>
                  </NuxtLink>
                </v-col>
              </v-row>
            </div>
          </v-col>
        </v-row>
      </div>
    </section>

    <!-- О проекте with hover effects -->
    <section class="py-16 md:py-24">
      <v-row align="center" justify="center">
        <v-col cols="12" md="10" class="text-center">
          <h2 class="text-h2 font-weight-black mb-12 text-primary" style="font-family: 'Montserrat', sans-serif;">
            О Нас
          </h2>
          <v-row>
            <v-col cols="12" md="4" class="px-6">
              <v-card elevation="3" class="pa-6 h-100 rounded-xl" color="grey-lighten-4">
                <v-icon size="40" color="primary" class="mb-4">mdi-rocket-launch</v-icon>
                <div class="text-h5 font-weight-bold mb-4 text-primary">
                  Наша Миссия
                </div>
                <p class="text-body-1">
                  Мы стремимся помочь заказчикам найти ответственных исполнителей для своих задач, а исполнителям
                  стабильный источник заработка.
                </p>
              </v-card>
            </v-col>
            <v-col cols="12" md="4" class="px-6">
              <v-card elevation="3" class="pa-6 h-100 rounded-xl" color="primary" dark>
                <v-icon size="40" color="white" class="mb-4">mdi-eye-outline</v-icon>
                <div class="text-h5 font-weight-bold mb-4">
                  Наше Видение
                </div>
                <p class="text-body-1">
                  Быть самой эффективной и удобной платформой, соединяющей заказчиков с талантливыми фрилансерами для
                  успешной реализации любого вида работы.
                </p>
              </v-card>
            </v-col>
            <v-col cols="12" md="4" class="px-6">
              <v-card elevation="3" class="pa-6 h-100 rounded-xl" color="grey-lighten-4">
                <v-icon size="40" color="primary" class="mb-4">mdi-heart-outline</v-icon>
                <div class="text-h5 font-weight-bold mb-4 text-primary">
                  Наши Ценности
                </div>
                <p class="text-body-1">
                  Инновации, качество и преданность делу - основные принципы, которыми мы руководствуемся в нашей работе
                  каждый день.
                </p>
              </v-card>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </section>

    <!-- Преимущества with card effects -->
    <section class="py-16 md:py-24 bg-gradient-to-b from-gray-100 to-white">
      <v-row align="center" justify="center">
        <v-col cols="12" md="10" class="text-center">
          <h2 class="text-3xl md:text-4xl font-bold text-center text-gray-900 mb-12 md:mb-16 px-4">Преимущества</h2>
          <v-row>
            <v-col v-for="(advantage, index) in advantages" :key="index" cols="12" md="4" class="px-6">
              <div
                class="bg-white p-6 md:p-8 rounded-2xl shadow-lg hover:shadow-2xl transition-all duration-500 transform hover:-translate-y-2 border border-indigo-50 h-full"
                :style="`transition-delay: ${index * 100}ms`">
                <div class="text-4xl md:text-5xl mb-4 md:mb-6">{{ advantage.icon }}</div>
                <h3 class="text-xl md:text-2xl font-semibold mb-3 md:mb-4">{{ advantage.title }}</h3>
                <p class="text-base md:text-lg text-gray-600">{{ advantage.description }}</p>
              </div>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </section>

    <!-- Отзывы with card rotation -->
    <section class="py-16 md:py-24">
      <v-row align="center" justify="center">
        <v-col cols="12" md="10" class="text-center">
          <h2 class="text-3xl md:text-4xl font-bold text-center text-gray-900 mb-12 md:mb-16 px-4">Отзывы</h2>
          <v-row>
            <v-col v-for="review in reviews" :key="review.id" cols="12" sm="6" md="4" class="px-4">
              <div
                class="bg-white p-6 md:p-8 rounded-2xl shadow-lg hover:shadow-2xl transition-all duration-300 transform hover:rotate-1 border border-indigo-50 h-full">
                <div class="flex items-center gap-4 mb-6">
                  <div
                    class="w-12 h-12 md:w-16 md:h-16 rounded-full bg-gradient-to-r from-indigo-500 to-indigo-600 flex items-center justify-center">
                    <span class="text-xl md:text-2xl font-semibold text-white">{{ review.name.charAt(0) }}</span>
                  </div>
                  <div>
                    <h3 class="text-lg md:text-xl font-semibold text-gray-900">{{ review.name }}</h3>
                    <p class="text-sm md:text-base text-indigo-600">{{ review.position }}</p>
                  </div>
                </div>
                <p class="text-base md:text-lg text-gray-600 italic">{{ review.text }}</p>
                <div class="flex text-yellow-400 mt-4 md:mt-6 text-xl md:text-2xl">
                  <span v-for="star in review.rating" :key="star"
                    class="transform hover:scale-125 transition-transform">★</span>
                </div>
              </div>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </section>

    <!-- Projects/Specialists Section -->
    <section class="py-16 md:py-24 bg-gradient-to-b from-gray-100 to-white" v-if="currentRole === 'worker'">
      <v-row align="center" justify="center">
        <v-col cols="12" md="10" class="text-center">
          <h2 class="text-3xl md:text-4xl font-bold text-center text-gray-900 mb-12 md:mb-16 px-4">
            {{ currentRole === 'worker' ? 'Доступные проекты' : '' }}
          </h2>
          <v-row>
            <v-col v-for="project in projects" :key="project.id" cols="12" sm="6" md="4" class="px-4">
              <div
                class="bg-white rounded-2xl shadow-lg overflow-hidden group hover:shadow-2xl transition-all duration-300 h-full">
                <div class="p-6 md:p-8">
                  <h3 class="text-xl md:text-2xl font-semibold mb-3 md:mb-4 group-hover:text-indigo-600 transition-colors">
                    {{ project.title }}</h3>
                  <p class="text-base md:text-lg text-gray-600 mb-4 md:mb-6">{{ project.description }}</p>
                  <div class="flex flex-wrap gap-2 mb-4">
                    <span v-for="tag in project.tags" :key="tag"
                      class="px-3 py-1.5 bg-indigo-50 text-indigo-800 rounded-full text-sm font-medium group-hover:bg-indigo-100 transition-colors">
                      {{ tag }}
                    </span>
                  </div>
                  <div class="text-lg font-semibold text-indigo-600">
                    {{ currentRole === 'worker' ? project.payment : `Рейтинг: ${project.rating}` }}
                  </div>
                </div>
              </div>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </section>

    <!-- Call to Action -->
    <section class="py-16 md:py-24 bg-gradient-to-r from-indigo-600 to-indigo-800 text-white relative overflow-hidden">
      <div
        class="absolute inset-0 bg-[url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAiIGhlaWdodD0iNjAiIHZpZXdCb3g9IjAgMCA2MCA2MCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48ZyBmaWxsPSJub25lIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiPjxwYXRoIGQ9Ik0zNiAxOGMzLjMxIDAgNiAyLjY5IDYgNnMtMi42OSA2LTYgNi02LTIuNjktNi02IDIuNjktNiA2LTZ6IiBzdHJva2U9InJnYmEoMjU1LDI1NSwyNTUsMC4xKSIgc3Ryb2tlLXdpZHRoPSIyIi8+PC9nPjwvc3ZnPg==')] opacity-10">
      </div>
      <v-container class="relative">
        <div class="text-center max-w-3xl mx-auto px-4">
          <h2 class="text-3xl md:text-4xl font-bold mb-6 md:mb-8">
            {{ currentRole === 'worker' ? 'Начните зарабатывать' : 'Найдите исполнителя' }}
          </h2>
          <p class="text-xl md:text-2xl mb-8 md:mb-12 text-indigo-100">
            {{ currentRole === 'worker'
              ? 'Присоединяйтесь к тысячам профессионалов уже сегодня'
              : 'Реализуйте ваши проекты с помощью лучших специалистов' }}
          </p>
          <div class="flex flex-col sm:flex-row justify-center gap-4 md:gap-6">
            <NuxtLink to="/sign"
              class="group bg-white text-indigo-600 px-6 md:px-8 py-3 md:py-4 rounded-full text-base md:text-lg font-medium hover:bg-indigo-50 transition-all duration-300 hover:shadow-xl hover:-translate-y-1 inline-flex items-center justify-center gap-2">
              Войти
              <span class="group-hover:translate-x-1 transition-transform duration-300">→</span>
            </NuxtLink>
            <NuxtLink to="/reg"
              class="group bg-indigo-500 text-white px-6 md:px-8 py-3 md:py-4 rounded-full text-base md:text-lg font-medium hover:bg-indigo-400 transition-all duration-300 hover:shadow-xl hover:-translate-y-1 inline-flex items-center justify-center gap-2">
              Регистрация
              <span class="group-hover:translate-x-1 transition-transform duration-300">→</span>
            </NuxtLink>
          </div>
        </div>
      </v-container>
    </section>
  </div>
</template>

<style>
.animate-fade-in {
  animation: fadeIn 1s ease-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>