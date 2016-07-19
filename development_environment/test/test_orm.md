# Тестирование ORM (Object-Relational Mapping (минимальный набор) #

---

## Алгоритм ##

* Выборка данных запоминаем кол-во записей
* Добавляем записи(один или неск) - коммит
* Опять выборка(с новой сессии), кол-во должно быть больше на кол-во добаленных
* Потом из выбранных редактируем наши записи - коммит
* Опять выборка(с новой сессии), проверяем что поменялись наши записи
* Удаляем наши записи - коммит
* Опять выборка(с новой сессии), проверяем что наших записей нет

## Пример ##

{%ace edit=false, lang='csharp', check=true, theme='coffee'%}

[Test]
public void TestViewAddEditDelete(){

const string name1 = "Test1";
const string name2 = "Test2";
//Assert.Fail("need uncomment and refactor");
//select groups
            mView.SelectGroups();
            int firstCount = mView.GroupsView.Count;

            Console.WriteLine(@"=== ADD ===");
            //Add new
            mView.NewGroup();
            mView.CurrentGroup.GroupName = name1;
            mView.CurrentGroup.UnitItemProp = mView.UnitItems.First();
            mView.CurrentGroup.GroupType = mView.GroupTypes.First();
            mView.SaveChanges();

            Console.WriteLine(@"=== ADD ===");
            mView.NewGroup();
            mView.CurrentGroup.GroupName = name2;
            mView.CurrentGroup.UnitItemProp = mView.UnitItems.First();
            mView.CurrentGroup.GroupType = mView.GroupTypes.First();

            SubGroup subGroup = new SubGroup();
            subGroup.ParamValue = "p1";
            subGroup.GroupProp = mView.CurrentGroup;
            subGroup.SubGroupDetails = new Iesi.Collections.Generic.HashedSet<SubGroupDetail>();
            mView.CurrentGroup.InitSubGroups();
            mView.CurrentGroup.SubGroups.Add(subGroup);

            SubGroupDetail detail = SubGroupDetail.Create(subGroup, new ComplexArt(mView.Artikls.First(), null), 1, "");
            subGroup.SubGroupDetails.Add(detail);

            detail = SubGroupDetail.Create(subGroup, new ComplexArt(mView.Artikls.Last(), null), 1, "");
            subGroup.SubGroupDetails.Add(detail);

            mView.SaveChanges();

            //edit
            Console.WriteLine(@"=== EDIT ===");
            mView.CurrentGroup = ((IEnumerable<Group>)mView.GroupsView.SourceCollection).Where(item => item.GroupName == name1).First();
            mView.CurrentGroup.InnerGroup = !mView.CurrentGroup.InnerGroup;
            mView.SaveChanges();

            Console.WriteLine(@"=== EDIT ===");
            mView.CurrentGroup = ((IEnumerable<Group>)mView.GroupsView.SourceCollection).Where(item => item.GroupName == name2).First();
            mView.CurrentGroup.InnerGroup = !mView.CurrentGroup.InnerGroup;
            mView.SaveChanges();

            //delete
            Console.WriteLine(@"=== DELETE ===");
            mView.DeleteGroup(((IEnumerable<Group>)mView.GroupsView.SourceCollection).Where(item => item.GroupName == name1).First());
            Console.WriteLine(@"=== DELETE ===");
            mView.DeleteGroup(((IEnumerable<Group>)mView.GroupsView.SourceCollection).Where(item => item.GroupName == name2).First());

            ////check at fin
            mView.SelectGroups();
            Assert.AreEqual(firstCount, mView.GroupsView.Count,"record count before check and after aren't equal");
        }

{%endace%}