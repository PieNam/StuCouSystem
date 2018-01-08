#include<stdio.h>
#include<string.h>

int main(void)
{
	int opr, oprs, flag = 1, flags = 1;
	char stuId[18], stuName[18], stuSex[18], tstuId[18], tstuName[18], tstuSex[18];
	char couId[18], couName[18];
	int couStuNum, couStuIn, aveScore;
	int stuScore, tstuScore;
	char number[18];
	int sure;
	FILE * fptr, * ftptr;

	begin:
	
	printf("*************************欢迎您使用学生信息管理系统*************************\n");
	printf("*                                                                          *\n");
	printf("*                                                                          *\n");
	printf("*                              1.学生相关操作                              *\n");
	printf("*                              2.课程相关操作                              *\n");
	printf("*                              3.选课相关操作                              *\n");
	printf("*                              0.退出系统                                  *\n");
	printf("*                                                                          *\n");
	printf("*                                                                          *\n");
	printf("*************************请输入您想要进行的操作序号*************************\n");
	
	for (int i = 0; i < 18; i++)
	{
		stuId[i] = '\0'; stuName[i] = '\0'; stuSex[i] = '\0';
		tstuId[i] = '\0'; tstuName[i] = '\0'; tstuSex[i] = '\0';
		couId[i] = '\0'; couName[i] = '\0'; number[i] = '\0';
	}
	stuScore = 0;
	tstuScore = 0;

	while (flag)
	{
		scanf("%d", &opr);
		if (!opr) return 0;
		else if (opr == 1)
		{
			printf("********************************学生相关操作********************************\n");
			printf("*                                                                          *\n");
			printf("*                             1.添加学生信息                               *\n");
			printf("*                             2.删除学生信息                               *\n");
			printf("*                             3.更改学生信息                               *\n");
			printf("*                             4.查看学生信息                               *\n");
			printf("*                             5.返回上一级                                 *\n");
			printf("*                             0.退出系统                                   *\n");
			printf("*                                                                          *\n");
			printf("*************************请输入您想要进行的操作序号*************************\n");

			while (flags)
			{
				scanf("%d", &oprs);
				switch (oprs)
				{
					case 0: return 0;
					case 1:
					{
						printf("请按照学号 姓名 性别顺序输入学生信息，每名学生占一行,以EOF结束录入。\n");
						printf("学号        姓名        性别\n");
						if ((fptr = fopen("stuInfo.txt", "a")) != NULL)
						{
							scanf("%s%s%s", stuId, stuName, stuSex);
							while (!feof(stdin))
							{
								fprintf(fptr, "%-18s%-18s%-18s\n", stuId, stuName, stuSex);
								scanf("%s%s%s", stuId, stuName, stuSex);
							}
						}
						fclose(fptr);
						printf("录入学生信息完毕，为您跳转到首页……\n\n");
						goto begin;
						break;
					}
					case 2:
					{
						printf("若档案中有此学生，其信息将被删除，否则您的操作不产生任何影响。\n");
						printf("请输入您要删除信息的学生的学号：\n");
						scanf("%s", number);
						printf("您确定要将学号为 %s 的学生的全部信息删除吗？1.确定 0.取消\n", number);
						printf("请输入选项序号1/0：\n");
						scanf("%d", &sure);
						if (sure)
						{
							fptr = fopen("stuInfo.txt", "r");
							ftptr = fopen("tmp.txt", "a");
							if ((fptr != NULL) && (ftptr != NULL))
							{
								fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
								while ((strcmp(stuId, number)) && (!feof(fptr)))
								{
									fprintf(ftptr, "%-18s%-18s%-18s\n", stuId, stuName, stuSex);
									fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
								}
								fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
								while (!feof(fptr))
								{
									fprintf(ftptr, "%-18s%-18s%-18s\n", stuId, stuName, stuSex);
									fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
								}
							}
							fclose(fptr);
							fclose(ftptr);
							remove("stuInfo.txt");
							rename("tmp.txt", "stuInfo.txt");
							printf("删除学生信息成功，为您跳转到首页……\n\n");
						}
						goto begin;
						break;
					}
					case 3:
					{
						printf("若档案中有此学生，将重新录入其信息，否则将您录入的信息新增到档案中。\n");
						printf("请输入您要修改信息的学生档案中的学号：\n");
						scanf("%s", number);
						printf("请按照学号 姓名 性别顺序输入该学生更新后的完整信息。\n");
						printf("学号        姓名        性别\n");
						scanf("%s%s%s", tstuId, tstuName, tstuSex);
						printf("您确定要更新该学生信息吗？1.确定 0.取消\n", number);
						printf("请输入选项序号1/0：\n");
						scanf("%d", &sure);
						if (sure)
						{
							fptr = fopen("stuInfo.txt", "r");
							ftptr = fopen("tmp.txt", "a");
							if ((fptr != NULL) && (ftptr != NULL))
							{
								fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
								while ((strcmp(stuId, number)) && (!feof(fptr)))
								{
									fprintf(ftptr, "%-18s%-18s%-18s\n", stuId, stuName, stuSex);
									fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
								}
								fprintf(ftptr, "%-18s%-18s%-18s\n", tstuId, tstuName, tstuSex);
								fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
								while (!feof(fptr))
								{
									fprintf(ftptr, "%-18s%-18s%-18s\n", stuId, stuName, stuSex);
									fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
								}
							}
							fclose(fptr);
							fclose(ftptr);
							remove("stuInfo.txt");
							rename("tmp.txt", "stuInfo.txt");
							printf("学生信息更改成功，为您跳转到首页……\n\n");
						}
						goto begin;
						break;
					}
					case 4:
					{
						int flag = 0;
						printf("若档案中有重复学号或姓名的，将显示档案中位置靠前的学生信息。\n");
						printf("请选择您要使用的学生查询模式：1.按学号查询 2.按姓名查询：\n");
						scanf("%d", &sure);
						if (sure == 1)
						{
							printf("请输入您要查询的学生的学号：\n");
							scanf("%s", number);
							if ((fptr = fopen("stuInfo.txt", "r")) != NULL)
							{
								while (!feof(fptr))
								{
									fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
									if (!strcmp(stuId, number))
									{
										flag = 1;
										break;
									}
								}
								if (flag)
								{
									printf("档案中对应学生信息为：\n%-18s%-18s%-18s\n", stuId, stuName, stuSex);
									printf("学生信息查询完毕，为您跳转到首页……\n\n");
								}
								else printf("档案中没有找到对应信息，为您跳转到首页……\n\n");
							}
						}
						else if (sure == 2)
						{
							printf("请输入您要查询的学生的姓名（大小写敏感）：\n");
							scanf("%s", tstuName);
							if ((fptr = fopen("stuInfo.txt", "r")) != NULL)
							{
								while (!feof(fptr))
								{
									fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
									if (!strcmp(stuName, tstuName))
									{
										flag = 1;
										break;
									}
								}
								if (flag)
								{
									printf("档案中对应学生信息为：\n%-18s%-18s%-18s\n", stuId, stuName, stuSex);
									printf("学生信息查询完毕，为您跳转到首页……\n\n");
								}
								else printf("档案中没有找到对应信息，为您跳转到首页……\n\n");
							}
						}
						goto begin;
						break;
					}
					case 5:
					{
						goto begin;
						break;
					}
					default:
					{
						printf("*************************请重新输入正确的操作序号：*************************\n");
						continue;
					}
				}
			}
		}
		else if (opr == 2)
		{
			printf("********************************课程相关操作********************************\n");
			printf("*                                                                          *\n");
			printf("*                             1.添加课程信息                               *\n");
			printf("*                             2.删除课程信息                               *\n");
			printf("*                             3.更改课程信息                               *\n");
			printf("*                             4.查看课程信息                               *\n");
			printf("*                             5.返回上一级                                 *\n");
			printf("*                             0.退出系统                                   *\n");
			printf("*                                                                          *\n");
			printf("*************************请输入您想要进行的操作序号*************************\n");

			while (flags)
			{
				scanf("%d", &oprs);
				switch (oprs)
				{
					case 0: return 0;
					case 1:
					{
						printf("请按照课程编号 课程名称 课程人数顺序输入课程信息。\n");
						printf("课程编号    课程名称    课程人数\n");
						scanf("%s%s%d", couId, couName, &couStuNum);
						char filename[36] = { '\0' };
						strcat(filename, couName);
						strcat(filename, ".txt");
						if (access(filename, 0) == 0) printf("该课程已存在，录入失败，为您跳转到首页……\n");
						else
						{
							if ((fptr = fopen(filename, "w")) != NULL)
								fprintf(fptr, "%s\n%s\n%d\n0\n0\n", couId, couName, couStuNum);
							fclose(fptr);
							printf("课程信息添加成功，为您跳转到首页……\n\n");
						}
						goto begin;
						break;
					}
					case 2:
					{
						printf("若档案中有此课程，其信息将被删除，否则您的操作不产生任何影响。\n");
						printf("请输入您要删除的课程名（大小写敏感）：\n");
						scanf("%s", couName);
						printf("您确定要将学号为 %s 的学生的全部信息删除吗？1.确定 0.取消\n", number);
						printf("请输入选项序号1/0：\n");
						scanf("%d", &sure);
						if (sure)
						{
							char filename[36] = { '\0' };
							strcat(filename, couName);
							strcat(filename, ".txt");
							remove(filename);
							printf("删除课程信息成功，为您跳转到首页……\n\n");
						}
						goto begin;
						break;
					}
					case 3:
					{
						printf("若档案中有此课程，将重新录入其信息，否则您的操作不产生任何影响。\n");
						printf("请输入您要修改信息的课程档案中的名称（大小写不敏感）：\n");
						scanf("%s", couName);
						char filename[36] = { '\0' };
						strcat(filename, couName);
						strcat(filename, ".txt");
						if (access(filename, 0) == -1) printf("该课程不存在，为您跳转到首页……\n");
						else
						{
							fptr = fopen(filename, "r");
							fscanf(fptr,"%s%s%d%d%d", couId, couName, &couStuNum, &couStuIn, &aveScore);
							printf("请按照课程编号 课程名称 课程人数顺序输入新的课程信息。\n");
							printf("课程编号    课程名称    课程人数\n");
							scanf("%s%s%d", couId, couName, &couStuNum);
							if ((ftptr = fopen("tmp.txt", "w"))!=NULL)
							{
								fprintf(ftptr, "%s\n%s\n%d\n%d\n%d\n", couId, couName, couStuNum, couStuIn, aveScore);
								fscanf(fptr, "%s%d", stuId, &stuScore);
								while (!feof(fptr))
								{
									fprintf(ftptr, "%-18s%d", stuId, stuScore);
									fscanf(fptr, "%s%d", stuId, &stuScore);
								}
								fclose(fptr);
								fclose(ftptr);
								remove(filename);
								char newfilename[36] = { '\0' };
								strcat(newfilename, couName);
								strcat(newfilename, ".txt");
								rename("tmp.txt", newfilename);
								printf("课程信息更改成功，为您跳转到首页……\n\n");
							}
						}
						goto begin;
						break;
					}
					case 4:
					{
						printf("请输入您要查看信息的课程档案中的名称（大小写不敏感）：\n");
						scanf("%s", couName);
						char filename[36] = { '\0' };
						strcat(filename, couName);
						strcat(filename, ".txt");
						if (access(filename, 0) == -1) printf("该课程不存在，为您跳转到首页……\n");
						else
						{
							if ((fptr = fopen(filename, "r")) != NULL)
							{
								fscanf(fptr, "%s%s%d%d%d", couId, couName, &couStuNum, &couStuIn, &aveScore);
								fclose(fptr);
								printf("课程信息如下：\n课程编号：%s 课程名称：%s\n课程容量：%d 已选人数：%d 平均分：%d\n", couId, couName, couStuNum, couStuIn, aveScore);
								printf("课程信息查询成功，为您跳转到首页……\n\n");
							}
						}
						goto begin;
						break;
					}
					case 5:
					{
						goto begin;
						break;
					}
					default:
					{
						printf("*************************请重新输入正确的操作序号：*************************\n");
						continue;
					}
				}
			}
		}
		else if (opr == 3)
		{
			printf("********************************选课相关操作********************************\n");
			printf("*                                                                          *\n");
			printf("*                             1.选课                                       *\n");
			printf("*                             2.退选                                       *\n");
			printf("*                             3.成绩录入                                   *\n");
			printf("*                             4.查看选课信息                               *\n");
			printf("*                             5.返回上一级                                 *\n");
			printf("*                             0.退出系统                                   *\n");
			printf("*                                                                          *\n");
			printf("*************************请输入您想要进行的操作序号*************************\n");

			scanf("%d", &oprs);
			switch (oprs)
			{
				case 0: return 0;
				case 1:
				{
					printf("请输入选课学生的学号：\n");
					scanf("%s", tstuId);
					fptr = fopen("stuInfo.txt", "r");
					int found = 0;
					while (!feof(fptr))
					{
						fscanf(fptr, "%s%s%s", stuId, stuName, stuSex);
						if (!strcmp(stuId, tstuId))
						{
							found = 1;
							break;
						}
					}
					fclose(fptr);
					if (!found) printf("档案中查无此学生，选课失败，为您跳转到首页……\n\n");
					if (found)
					{
						printf("请输入目标课程名称（大小写不敏感）：\n");
						scanf("%s", couName);
						char filename[36] = { '\0' };
						strcat(filename, couName);
						strcat(filename, ".txt");
						if (access(filename, 0) == -1) printf("档案中查无此课程，选课失败，为您跳转到首页……\n\n");
						if (access(filename, 0) == 0)
						{
							fptr = fopen(filename, "r");
							fscanf(fptr, "%s%s%d%d%d", couId, couName, &couStuNum, &couStuIn, &aveScore);
							if (couStuNum < (couStuIn + 1))
							{
								printf("该课程人数已满，选课失败，为您跳转到首页……\n\n");
								fclose(fptr);
							}
							else
							{
								ftptr = fopen("tmp.txt", "w");
								fprintf(ftptr, "%s\n%s\n%d\n%d\n%d\n", couId, couName, couStuNum, couStuIn+1, ((aveScore*couStuIn)/(couStuIn+1)));
								fscanf(fptr, "%s%d", tstuId, &tstuScore); 
								while (!feof(fptr))
								{
									fprintf(ftptr, "%-18s%d\n", tstuId, tstuScore);
									fscanf(fptr, "%s%d", tstuId, &tstuScore);
								}
								fprintf(ftptr, "%-18s%d\n", stuId, stuScore);
								fclose(fptr);
								fclose(ftptr);
								remove(filename);
								rename("tmp.txt", filename);
								printf("选课成功，为您跳转到首页……\n\n");
							}
						}
					}
					goto begin;
					break;
				}
				case 2:
				{
					printf("请输入目标课程的名称（大小写不敏感）：\n");
					scanf("%s", couName);
					char filename[36] = { '\0' };
					strcat(filename, couName);
					strcat(filename, ".txt");
					if (access(filename, 0) == -1) printf("档案中查无此课程，选课失败，为您跳转到首页……\n\n");
					if (access(filename, 0) == 0)
					{
						printf("请输入要退选的学生的学号：\n");
						scanf("%s", tstuId);
						fptr = fopen(filename, "r");
						fscanf(fptr, "%s%s%d%d%d", couId, couName, &couStuNum, &couStuIn, &aveScore);
						int found = 0;
						while (!feof(fptr))
						{
							fscanf(fptr, "%s%d", stuId, &stuScore);
							if (!strcmp(stuId, tstuId))
							{
								found = 1;
								break;
							}
						}
						if (!found)
						{
							printf("档案中查无此学生，为您跳转到首页……\n");
							fclose(fptr);
						}
						if (found)
						{
							ftptr = fopen("tmp.txt", "w");
							fprintf(ftptr, "%s\n%s\n%d\n%d\n%d\n", couId, couName, couStuNum, couStuIn-1, ((aveScore*couStuIn-stuScore)/(couStuIn-1)));
							rewind(fptr);
							fscanf(fptr, "%s%s%d%d%d", couId, couName, &couStuNum, &couStuIn, &aveScore);
							fscanf(fptr, "%s%d", stuId, &stuScore);
							while ((strcmp(stuId, tstuId)) && (!feof(fptr)))
							{
								fprintf(ftptr, "%-18s%d\n", stuId, stuScore);
								fscanf(fptr, "%s%d", stuId, &stuScore);
							}
							while (!feof(fptr))
							{
								fscanf(fptr, "%s%d", stuId, &stuScore);
								if (feof(fptr)) break;
								fprintf(ftptr, "%-18s%d\n", stuId, stuScore);
							}
							fclose(fptr);
							fclose(ftptr);
							remove(filename);
							char newfilename[36] = { '\0' };
							strcat(newfilename, couName);
							strcat(newfilename, ".txt");
							rename("tmp.txt", newfilename);
							printf("课程信息更改成功，为您跳转到首页……\n\n");
						}
					}
					goto begin;
					break;
				}
				case 3:
				{
					printf("请输入目标课程的名称（大小写不敏感）：\n");
					scanf("%s", couName);
					char filename[36] = { '\0' };
					strcat(filename, couName);
					strcat(filename, ".txt");
					if (access(filename, 0) == -1) printf("档案中查无此课程，查询失败，为您跳转到首页……\n\n");
					if (access(filename, 0) == 0)
					{
						printf("请输入目标学生的学号：\n");
						scanf("%s", tstuId);
						fptr = fopen(filename, "r");
						fscanf(fptr, "%s%s%d%d%d", couId, couName, &couStuNum, &couStuIn, &aveScore);
						int found = 0;
						while (!feof(fptr))
						{
							fscanf(fptr, "%s%d", stuId, &stuScore);
							if (!strcmp(stuId, tstuId))
							{
								found = 1;
								break;
							}
						}
						if (!found) printf("档案中查无此学生，成绩录入失败，为您跳转到首页……\n\n");
						if (found)
						{
							printf("请输入该学生在该课程的成绩：\n");
							scanf("%d", &tstuScore);
							ftptr = fopen("tmp.txt", "w");
							fprintf(ftptr, "%s\n%s\n%d\n%d\n%d\n", couId, couName, couStuNum, couStuIn, ((aveScore*couStuIn - stuScore + tstuScore) / couStuIn));
							rewind(fptr);
							fscanf(fptr, "%s%s%d%d%d", couId, couName, &couStuNum, &couStuIn, &aveScore);
							fscanf(fptr, "%s%d", stuId, &stuScore);
							while ((strcmp(stuId, tstuId)) && (!feof(fptr)))
							{
								fprintf(ftptr, "%-18s%d\n", stuId, stuScore);
								fscanf(fptr, "%s%d", stuId, &stuScore);
							}
							fprintf(ftptr, "%-18s%d\n", stuId, tstuScore);
							while (!feof(fptr))
							{
								fscanf(fptr, "%s%d", stuId, &stuScore);
								if (feof(fptr)) break;
								fprintf(ftptr, "%-18s%d\n", stuId, stuScore);
							}
							fclose(fptr);
							fclose(ftptr);
							remove(filename);
							char newfilename[36] = { '\0' };
							strcat(newfilename, couName);
							strcat(newfilename, ".txt");
							rename("tmp.txt", newfilename);
							printf("课程信息更改成功，为您跳转到首页……\n\n");
						}
					}
					goto begin;
					break;
				}
				case 4:
				{
					printf("请输入目标课程的名称（大小写不敏感）：\n");
					scanf("%s", couName);
					char filename[36] = { '\0' };
					strcat(filename, couName);
					strcat(filename, ".txt");
					if (access(filename, 0) == -1) printf("档案中查无此课程，查询失败，为您跳转到首页……\n\n");
					if (access(filename, 0) == 0)
					{
						fptr = fopen(filename, "r");
						fscanf(fptr, "%s%s%d%d%d", couId, couName, &couStuNum, &couStuIn, &aveScore);
						printf("已选这门课程的学生学号及成绩信息如下：\n学号              成绩\n");
						fscanf(fptr, "%s%d", stuId, &stuScore);
						while (!feof(fptr))
						{
							printf("%-18s%d\n", stuId, stuScore);
							fscanf(fptr, "%s%d", stuId, &stuScore);
						}
						fclose(fptr);
						printf("选课信息查询完毕，为您跳转到首页……\n\n");
					}
					goto begin;
					break;
				}
				case 5:
				{
					goto begin;
					break;
				}
				default:
				{
					printf("*************************请重新输入正确的操作序号：*************************\n");
					continue;
				}
			}
		}
		else
		{
			printf("*************************请重新输入正确的操作序号：*************************\n");
			continue;
		}
	}
	return 0;
}
