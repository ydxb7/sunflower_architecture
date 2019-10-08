graph TD

GardenActivity[GardenActivity] -->|Navigation graph| HomeViewPagerFragment{HomeViewPagerFragment}

GardenPlantingAdapter --> |navigate with arg: palntId| PlantDetailFragment{PlantDetailFragment}

HomeViewPagerFragment --> ViewPager[ViewPager]

ViewPager --> |pageIndex=0| GardenFragment{GardenFragment}

GardenFragment --> |Add plant button click, navigate to| PlantListFragment

GardenFragment --> |ViewModel| GardenPlantingListViewModel[GardenPlantingListViewModel]

GardenPlantingListViewModel --> |LiveData| plantAndGardenPlantings[plantAndGardenPlantings]

GardenPlantingListViewModel --> |get plants|GardenPlantingRepository

plantAndGardenPlantings --> |update| GardenPlantingAdapter

ViewPager --> |pageIndex=1| PlantListFragment{PlantListFragment}

RecyclerView1 --> PlantAdapter

PlantAdapter --> |navigate with arg: palntId| PlantDetailFragment

PlantListFragment --> RecyclerView1[RecyclerView]

PlantListFragment --> PlantListViewModel

PlantListViewModel --> |LiveData| plants

plants --> |get plants|GardenPlantingRepository

GardenFragment --> RecyclerView[RecyclerView]

RecyclerView --> GardenPlantingAdapter

GardenPlantingDao --> GardenPlantingRepository

GardenPlantingDao --> Plant

PlantDetailFragment --> PlantDetailViewModel

PlantDetailViewModel --> |addPlantToGarden|GardenPlantingRepository

PlantDetailViewModel --> |getPlant|GardenPlantingRepository

PlantDetailFragment --> |navigateUp| HomeViewPagerFragment

PlantDetailFragment --> |navigateUp| GardenFragment

PlantDetailFragment --> |action_share| shareIntent